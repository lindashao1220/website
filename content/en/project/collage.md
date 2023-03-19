---
title: "Photo Collage"
date: 2022-11-17T22:51:49+08:00
draft: false
cover:
    image: ../img/collage.gif
    alt: 'collge'
    caption: "project screenshots gif"
images:
- img/collage.gif
---
In the physical world, here and there are never the same. However, this website can be a space of encounter, a plaza where here and there converge. 

People can get on the website at the same time and take pictures of a part of their face by following the instruction. Ultimately, they can see a photo face collage of themselves and the other online users.

[This version ](https://photocollage.glitch.me/) is for when you get online with friends together.

[This version](https://facecollageforopenproject.glitch.me/) is updated version, and you can enjoy the photo collage yourself 👣



## Abstract

Photo Collage is a website that shows the connectivity between people, which allows users to take pictures of their faces and then generates photo collages of their faces along with those of other users, both current and previous, on a rolling basis.

In the physical world, "here" and "there" are not the same. However, this project can provide a space for connection. Regardless of how far apart people may be geographically or emotionally, they can come together on this website by sharing a part of their face. Surprisingly, even with different races, genders, nationalities, and personalities, the final result of the photo collage doesn’t look completely weird. In contrast, it even looks consistent and cute.

## Project Description

Photo Collage is an online platform that demonstrates the interconnectedness of its users by enabling them to capture images of their own faces, and subsequently, create photo collages that feature both past and present users on a continuous basis.

Amidst the COVID outbreak in Shanghai, I experienced a sense of isolation and detachment among people. This inspired me to initiate a project that leverages the power of web browsing to foster connection and demonstrate the interdependence of individuals. The project invites the audience to take part by contributing photographs of their facial features and enjoying the photo collages to feel that sense of connectedness to people. 

I used [**socket.io**](http://socket.io) to make communication between clients possible. Also, I implemented machine learning(**ml5.js**) to help the users take photos and a **database**(firebase) to store all the data images and pull those data to the front end to achieve the rolling-basis photo collage effect. 

## Visual Documentation

![the interface](../img/interface.png)


## Context and Perspective

My project can be considered situated in the field of net/web art. Inspired by this quote, “the website can be as a space of encounter, a plaza where here and there converge. The browser then is a window onto this plaza. What can people see behind the glass? And if someone climbs through it, how can people interact with fellow humans that found their way (t)here, too?”, I, therefore, used the web as a tool for artistic and social purposes to show the connectiveness between people.

This project was first developed during the COVID-19 pandemic period when people were physically and mentally separated from each other due to the lockdown and quarantine. However, I used the technology to connect strangers from different age ranges, countries, and races to randomly encounter and connect.

## Designs and Ideas

My idea is very consistent. In the beginning, I have a very clear goal of what I wanted to achieve, which is to implement the ml5.js, database and change the server-side allocate room code. Doing all these can help me increase the user experience. Also, I stick to using my minimalist style in my project.

However, I still made some little twitches in the design of my project.

1. My two buttons’ names used to be “snap” and “send”. However, during user testing, a lot of people find the buttons’ names very unintuitive. They cannot understand why the button is called “snap” without a real-time camera video placed on the interface. Therefore, eventually, I changed the two buttons to “capture” and “contribute”. The users have given camera permission to my website, so they can probably understand it better.
2. Since I was afraid people might accidentally click on the button, I made a lot of confirmation boxes(check it below in this video). My mentor Prof.Leon Eckert told me it is very annoying for him to close those confirmation boxes manually, so I decided just to leave those necessary pop-up windows like the user cannot submit an empty picture to the database. 


1. In terms of design, I have also made use of CSS breakpoints to make the web responsive and look good in different browser window sizes.



## Development and Technical Implementation

There are mainly three technical developments I made in my project, which are ml5.js, database, and room allocation rule on my server side.

1. ml5.js

![ml5](../img/ml5.png)
For my project, I experimented with several facial recognition APIs. While the first API I tested was only capable of detecting the central point of facial features, I aimed to obtain the minimum and maximum coordinates to capture the entire facial region. With Prof. Gohai's guidance, I was able to utilize the face API of ml5.js, which enabled me to achieve the desired detection effect.

After I finished detecting the part, I started working on cropping out the copying canvas’ pixels part and turning the image to the data URL to better store and send the image.



2. database(firebase)
![database](../img/databse.png)

To store and retrieve image data, I employed the firebase tool and followed a tutorial to learn the process. Although sending and receiving image data from the database was not challenging, the most difficult aspect was retrieving a random data string from the appropriate folder in the database and assembling all the items into an array. Afterward, I had to randomly select an item on the server side before sending it to the front end. And I did it by the code below (I took left eye as an example)

```jsx
let counter = 0;

let randomLefteyeItem;
let countLefteyeCur; 
let arrLefteye = [];

//get the current numbr of the file in database to allocate part
ref0.once('value').then((snapshot) => {
  countLefteyeCur = snapshot.numChildren();
  console.log("heyyyy i am always here", countLefteyeCur)
  counter = counter + 1;
})

//tuen all the data in database into an image array
  ref0.once('value').then((snapshot) => {
    let archivalLefteyeData = snapshot.val();

    let keys;
    let dataPoint;
    keys = Object.keys(archivalLefteyeData);
    for(let i = 0; i < keys.length; i++){
      let key = keys[i];
    dataPoint = archivalLefteyeData[key].imgChange;
    arrLefteye.push(dataPoint);
  }

//get a random image data and send it out
  let time = 5000 + Math.random() * 10000;
  setInterval(() => {
    randomIndex = Math.floor(Math.random() * arrLefteye.length);
    randomLefteyeItem = arrLefteye[randomIndex];
    // console.log(randomLefteyeItem); // prints a random value from the array
    socket.emit('archivalLefteyeData', randomLefteyeItem);
  }, time); 
})
```

3. room allocation rule
![allocation](../img/allocate.png)

I completely altered the working protocol for the server side. Previously, I utilized [socket.io](http://socket.io/) to group five individuals in a single room, and when someone vacated the room, new participants would take their place.

However, the rule has now changed. I have obtained a list of files in each folder in my database. The new allocation rule is to assign users to the part with the least number of files.


## User Testing

During the user testing sessions, I think most of the users know how to navigate the web page on their own. Still, I learned a lot from the user test session, and here are some key points that I changed:

1. The button names "contribute" and "send" should be changed to avoid confusion among users. Many users assume that "contribute" already includes the meaning of sending, so they don't understand the purpose of the "send" button.
2. The "cancel" button in the confirmation box does not function properly. Even if the user clicks "cancel," the code still captures their photos. Additionally, the confirmation box pops up multiple times, even if the user only clicked it once.
3. After users submit their photos, the same face part is captured again. However, it would be better if they could select a different part to capture after the first attempt.
4. Professor Moon suggested that it would be nice if all the collected photos had pixelated edges. Additionally, if the photos overlapped with each other, the effect would be even more interesting when added to the project.
5. Most users just think the photo collage they’ve seen is cute and they like it, however, very few amounts of them are thinking about the idea of “connectivity” behind it. Therefore, I decided to add a pop-up info box to my project, to make things clearer.


## Conclusion

Photo Collage is an online platform that allows users to take pictures of their faces, and subsequently, creates photo collages that feature both past and present users on a continuous basis. The project was inspired by the sense of isolation and detachment experienced by people amidst the COVID outbreak in Shanghai. The aim was to leverage the power of web browsing to foster connection and demonstrate the interdependence of individuals. The project invites the audience to take part by contributing photographs of their facial features and enjoying the photo collages to feel that sense of connectedness to people.

The project uses [socket.io](http://socket.io/) to enable communication between clients, ml5.js to facilitate facial recognition, and a database (firebase) to store all image data and pull it to the front end to achieve the rolling-basis photo collage effect. The goal of Photo Collage is to demonstrate the interconnectedness of its users by creating photo collages that feature both past and present users on a continuous basis.

I learned the ml5.js, database, and CSS breakpoint in this project. This project made me like coding more since I can always find a sense of achievement after I have done something new. I think it is pretty successful since I achieved all of my goals. There are still some small changes I can make though. To clarify, I have the potential to enhance the user-friendliness of the interface even further. As previously mentioned in the presentation, one approach could involve integrating a real-time video camera of a specific facial feature in the interface to create a more intuitive experience. Additionally, I could implement a face API to track user locations and document which individuals captured photos at specific sites, thus promoting a greater sense of connection😽

