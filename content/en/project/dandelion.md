---
title: "Dandelion"
date: 2023-3-17T22:51:49+08:00
draft: false
cover:
    image: ../img/dandelion.png
    alt: 'dandelion'
    # caption: ""
images:
- img/ok.gif
---
## Abstract

Dandelion is a meditative mobile web experience that uses interactive and nature-inspired elements to provide users with a calming escape from everyday stresses. By gently blowing into the microphone or swaying their phone, users can watch the petals of a dandelion flower dance and flutter off, transporting them into a tranquil mindset. The interactive experience encourages people to find peace in a simple and natural interaction with technology.

## Project Description

Dandelion is a mobile web experience designed to provide users with a meditative and calming escape from the stresses of everyday life. The concept behind the project is to create a digital experience that uses interactive and nature-inspired elements to encourage people to find peace and tranquility in their daily lives.

The project features a dandelion flower that responds to the user's gentle blowing into the microphone or swaying of the phone. As the user interacts with the flower, the petals dance and flutter off, creating a tranquil and peaceful atmosphere. The interactive experience is designed to be simple and natural, mimicking the calming effects of nature and allowing users to find a moment of relaxation and serenity in the midst of their busy lives.

The intention of the project is to promote mindfulness and well-being by using technology in a positive and uplifting way. By offering a digital escape that encourages users to engage with nature and their senses, Dandelion aims to provide a simple yet powerful tool for stress relief and relaxation.

## Visual Documentation

link: https://lindashao1220.github.io/OpenProjectDrawing/done1/

The phone’s interface:

![the interface](../img/1.png)

![interface](../img/2.png)

[RPReplay_Final1683818981.mov](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5707ce52-6f3d-4aa5-8b5c-9e040d542c8d/RPReplay_Final1683818981.mov)

The website interface:

![interface](../img/4.png)


## Context and Perspective

- Nostalgic association: dandelions often symbolize childhood innocence, wonder, and play. Interacting with a virtual dandelion in an immersive way can tap into nostalgic memories of making wishes and enjoying simple pleasures in nature. This can have a soothing, meditative effect on both the mind and body.
- Natural aesthetics and present-moment focus: The open-ended and non-pressured experience of playing and interacting with the virtual dandelion gives users the freedom to explore in a way that feels personally restorative. There are no rules or specific goals, just a chance to reconnect with a sense of childlike wonder and the simple joys of nature.
- The trend of  “applicationalise” physical things: There are apps like burning paper, 一炷香, and wooden fish, which are all very popular among Chinese teenagers. All the apps make the physical things display in a virtual way. It is very fun, and at the same time, it also makes things very accessible, since everyone has phones with them all the time.
- The trend of "applicationalising" physical things has become increasingly popular in recent years. This trend involves creating digital applications or apps that simulate physical objects or experiences. Apps like burning paper, 一炷香, and wooden fish have gained popularity among Chinese teenagers by allowing them to experience traditional practices in a digital format. This trend has several advantages. Firstly, it makes physical things more accessible to people. Almost everyone carries a smartphone with them all the time, so people can experience these things without having to physically be in a certain place or carry a physical object. Additionally, the apps can make these experiences more interactive and immersive by adding features such as sound and visual effects that may not be possible in real life.

![interface](../img/5.png)

## Designs and Ideas

I am inspired by the Murmer project, which is an interactive installation, and I want to create a phone version of it that can be accessible to everyone and provide an enjoyable experience.

[Murmur installation by Chevalvert, 2Roqs, Polygraphik, Splank, Reims – France](https://retaildesignblog.net/2013/10/01/murmur-installation-by-chevalvert-2roqs-polygraphik-splank-reims-france/)

and then I come up the idea of making a dandelion that can sway around and be blown by the users.

After that I first tried out different patterns of the petal, and this is my first try:

![interface](../img/6.png)

Apparently, it doesn’t look like a petal group at all, so I tried again using function, and then felt pretty satisfied with this petal work.

![interface](../img/7.png)


After that, I started to think what my dandelion as a whole should look like. I initially thought of my project as a flower that can be updated constantly. I envision that when users give different movements, it will result in different patterns of petals appearing. Like this:

![interface](../img/8.png)

{{< youtube gUZjVSDPFaE >}}

But then it looks a bit weird since the users cannot find any connections between their motion input and the visual output. Also, the petals will all disappear after one round of updates. So I decided to tweak the project a little. I start out by drawing this kind of inner petal.

{{< youtube W4vnW-k0U9g>}}


Gradually, I finished drawing the flower, and to make the movement of the flower more natural, I started to add some sin and cos waves into their movement. So it looks like this:

{{< youtube lnAulnqN59M >}}

After this, I started to add the stem of the flower and hoping it can get moving according to the tilting position of the phone. Also, I decided to make all the petals grow after they disappear, instead of just getting back instantly, and this is the final result:)

[Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7cde2aa4-2749-4349-bc9a-7310bf3e124b/Untitled.qt)

Last, I also added some particles to the project to make the color picking/color changing of the petal make more sense. So basically, the petal’s color will be updated according to the user's tilting position and input.

[Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d79be442-50a6-4e3a-9d6a-dfadd8d8187e/Untitled.qt)

## Development and Technical Implementation

I tried out using wechat mini app first, but failed… Since I cannot get the gyroscope value. So I decided to make a website for it.

![interface](../img/14.png)

After I tried making a website, there are two major changes that I met. One is to change all the functions into class, and another is to move all the things controlling the petals into the class Petal.

In terms of the first one, when I almost finish the prototype of the project and want to add more movement to each petal, I found it very hard to move on, since back then, my logic is to push all the things into an array and call the function. Therefore, I changed everything into my flower.

![interface](../img/15.png)

In terms of the second one, I controlled some of the petal movement outside of the class, and that causes a lot of problems since it would only run once. After Professor Gottfried’s advice and help, it works perfectly because the code is much more organized. I learned a lot, since now I understand all the code blocks have their own function, and I should try to make the most out of the function of it, instead of messing it around.

![interface](../img/16.png)

As for other exploration and changes I make. First, developing the particle system, I know the createVector and applyForce. Second, I try out the gyroscope using the phone. This is the first time I experiment things with a gyroscope and built things on a phone. It is a little bit hard, because I failed to give my phone the certificate to host the local website, so I have to push it to the git hub every time. Third, I have made use of the check if it is a phone device code, to make the project will only work on a phone.

![interface](../img/17.png)

## User Testing

I got a lot of feedback during the user testing part, and I have kept all of them down.

In terms of visuals and experience, I got this feedback:

1. make the dandelion sway when the user is tilting the phone, and match the dandelion’s movement with the movement of the phone
2. make the dandelion grow when it is all blown out instead of reappearing again
3. the particles can get down from one direction to another instead of everywhere
4. the background can be changed
5. the petals which are blown away should be moved away from the blowing direction

In terms of the concept, I got this feedback:

1. dandelion makes the user think of making a wish
2. language of flower: dandelions represent **the return of life, the rebirth of growth and green after a harsh winter, and a display of abundant strength and power**.
3. change the way how people interact with their phone 

## Revisions

Following the user testing phase, I made significant changes to my project. Specifically, I revised the design by incorporating the sway and growth of the dandelion, instead of having it return to its original position. I believe that this is a major modification, as it gives the dandelion a more natural appearance, and the growth aspect can signify rebirth.

Moreover, I took the opportunity to contemplate the significance of my project and what I aimed to convey with it. This helped me to better understand my initial motivation for embarking on this project. To gain more insight, I also explored other apps that share similar features with my dandelion, such as Wooden Fish.

In summary, I have refined my project both visually and technically based on user feedback and a deeper understanding of my objectives.

## Presentation

As for the final presentation, I think it works pretty well. [This](https://docs.google.com/presentation/d/1_wSiwPGCXFQVTPSPWQG4xJtaCkK4UWv4llZ9SVpzoAQ/edit#slide=id.g222ba973a63_0_86) is the slide I have prepared. 

There were several suggestions made during the development of my project. Firstly, there was a suggestion to consider how the project would be presented to users. Should it be designed for individual use on a phone, even in a gallery, or could it be installed as a physical installation with phones assembled on stands, on a surface resembling a digital field with dandelions?

Secondly, a suggestion was made to modify the behavior of the petals. Specifically, each petal object could have an individual threshold for flying away, so that they don't all fly away at once. 

Lastly, it was suggested that I add an instruction for the blowing function. Currently, users may not be aware that they can blow on the dandelions to activate this feature. By adding clear instructions, users can fully enjoy and engage with the interactive aspect of the project.

After the presentation, I have also made some further changes. So the petals will not fly away in groups of petals, but each petals will have its own threshold. Thanks for Leon’s suggestion and help✨

## Conclusion

Through the process of working on this project, I have gained a wealth of knowledge. One of the key lessons I learned in coding was the importance of maintaining a well-organized code structure. It's crucial to ensure that each code block is performing the specific task that it's intended for, instead of placing code blocks haphazardly and creating confusion.

Furthermore, I also learned that design is a complex process that requires a great deal of effort and experimentation. As a relatively inexperienced designer, I now understand that it may take numerous attempts and considerable thought to arrive at a successful design. It's vital to remain patient and persistent in the face of design challenges and to continue refining the design until it meets the desired standards.

In the future, I think I will be more critical about my project and be more patient with things.

Last but not least, special thanks to Gottfried and Leon!!!