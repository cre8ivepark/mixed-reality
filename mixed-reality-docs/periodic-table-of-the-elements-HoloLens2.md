---
title: Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2
description: Periodic Table of the Elements is an open-source sample app from Microsoft's Mixed Reality Design Labs where you can learn how to lay out an array of objects in 3D space with various surface types using an Object collection.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, sample app, controls
---



# Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2
Sharing the story of updating HoloLens app made with HoloToolkit(HTK) to use new Mixed Reality Toolkit v2(MRTK) which supports HoloLens 2's articulated hand tracking and eye tracking input

>[!NOTE]
>This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development. Our design-related articles and code will evolve as we make new discoveries.

[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs. The project, demonstrates how to use MRTK's building blocks to create HoloLens and Windows Mixed Reality experiences.

We published Mixed Reality Design Lab's Periodic Table of the Elements app for HoloLens and immersive headset back in 2015 to demonstrate how to create an end-to-end experience using HoloToolkit's building blocks. To fully leverage new articulated hand tracking and eye tracking input on HoloLens 2, we need to update HoloToolkit(HTK) to newly released Mixed Reality Toolkit(MRTK) v2.


![Period Table of the Elements app](images/640px-periodictable-hero.jpg)

## What is MRTK v2?

MRTK is a Microsoft driven open source project. MRTK-Unity provides a set of foundational components and features to accelerate mixed reality app development in Unity. The latest Release of MRTK v2 supports HoloLens/HoloLens 2, Windows Mixed Reality, and OpenVR platforms.
Since MRTK v2 is completely redesigned from the ground up, foundational components such as input system are not compatible with HoloToolkit. Because of this, you need to put some effort to upgrade HoloToolkit to MRTK. In this story, I'll show you how I updated HoloToolkit to MRTK and evolved the design to fully leverage hand tracking and eye tracking input.

## Getting new MRTK release packages

From MRTK GitHub repository, you can download MRTK release packages under 'Release' menu. You can also clone the repository. The branch name for the MRTK v2 is mrtk_release. If you want to get the latest features and components under active development, you can use mrtk_development branch. However, please keep in mind that development branch could be unstable and something might be broken.

![Release packages on MRTK GitHub]()

![MRTK release packages]()

There are two types of release packages. Foundation and Examples. Foundation package has core features and input system of MRTK. Optional Examples package contains example scenes and scripts that demonstrate the use of core features in the Foundation package. In the example scenes, you will be able to play with various types of new interaction building blocks and UI components. Below is one of the example scenes you can find in the Examples package.

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

Since we only need foundational components and building blocks for the project, we can download the Foundation package.


## Design

For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element. The surface of each box would be translucent so that the user could get a rough idea of the element's volume. With gaze and air tap, the user could open up a detailed view of each element. To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.

![Design sketch](images/640px-sketch20170406.jpg)<br>
*Design sketches*

In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space. The animated 3D electron model is displayed in the center area and can be viewed from different angles.

![Interaction](images/640px-periodictable-interaction.jpg)

![Prototypes](images/640px-periodictable-prototypes.jpg)<br>
*Interaction prototypes*

The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.

## Common controls and patterns used in this app

### Interactable object (button)

[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs. It is provided as a prefab/script which you can easily apply to any object. For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures. [Learn more](interactable-object.md)

![nteractable object](images/640px-periodictable-interactableobject.jpg)

### Object collection

[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes. It supports plane, cylinder, sphere and scatter. You can configure additional properties such as radius, number of rows and the spacing. [Learn more](object-collection.md)

![Object collection](images/640px-periodictable-collections.jpg)

### Fitbox

By default, holograms will be placed in the location where the user is gazing at the moment the application is launched. This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table. A fitbox allows a user to use gaze to determine the location where the hologram will be placed. It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## Technical details

You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## Application examples

Here are some ideas for what you could create by leveraging the components in this project.

### Stock data visualization app

Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data. This example uses the Object collection control to lay out stock data in a spherical shape. You can imagine a detail view where additional information about each stock could be displayed in an interesting way.

![Application example: Finance (1 of 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Application example: Finance (2 of 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*

### Sports app

This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.

![Application example: Sports (1 of 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Application example: Sports (2 of 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*

## About the author

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX Designer @Microsoft</td>
</tr>
</table>

## See also

* [Interactable object](interactable-object.md)
* [Object collection](object-collection.md)
