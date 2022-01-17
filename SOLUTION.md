## How long did it take you to complete this assignment?
It took me about 1.5 day to finish this assignment. I can take less time to develop it once I get used to using Vue again (Developed a front-end after 1.5 year).

## What about this assignment did you find most challenging?
Making the Split Stream responsive was challenging a bit.

## What about this assignment did you find unclear?
Initially was confused if i had to use image or video. Once figured that out was unsure what the step would be after selecting an option in the "Add Source" Modal. Usually there, would be a step in between selecting a source and adding the source on the left hand side to the list of sources.(Like in zoom, once you select screen share, there is a list on what part of the screen you want to share). I directly added to the the source list on the left hand side once clicked on an option

## What challenges did you face that you did not expect?
Did not find anything unexpected.

## Do you feel like this assignment has an appropriate level of difficulty?
Yes, it was. This assignment made me use most of the features of VueJS and CSS.

## Briefly explain your decisions to use tools, frameworks and libraries like React, Vue, etc.
Vue JS - makes it easy to make the application interactive.
Bootstrap - It has the grid system, which makes it easy to create different layouts and making it responsive. Also it has other pre-defined components - Modal, buttons.
Fontawesome - pre-defined classes for icons

## Did you make certain assumptions and decisions around the UI/UX? Please elaborate on your reasonings.

- The icons for layout configurations might not look great since I took a screenshot and used them.

- As mentioned before, after selecting an option for a source in the modal, since there is no intermediate step mentioned, I am programmaticaly adding a source on the left hand side list.

- Even if you select the same source on "add a new source" modal again and again, I am currently not performing validation for it since I am adding the sources programmatically.

- ssumed that the "chat, record, go live" belong to the whole screen (since they are in the middle of the screen) and not in LHS or RHS components of the screen. Only these buttons have text in bold (usually would ask the designer) 

- Since we are considering just 1 videofeed and 1 screenshare, using variables accordingly(eg: videoFeed.showOnStream and screenShare.showOnStream). Or else would had used generic variables in a real project. Right now minimizing the use of variable and operations.

- Assumed that images I will be getting will always be of the aspect ratio 16:9

- Added some styling to the buttons for hover.

- For the split screen (video feed and screenshare ) based on the wireframe (also by thinking by myself), the screenshare is never cropped since I assumed that it is more important to see the entire screen at all the time. For the video feed, the aspect ratio of the feed is maitained but only the window size of the feed ie 33%  of the stream size, and centered is shown ( the streamer will have to make sure that they are the centre of the video feed to be visible).

- The image size for camera.png is small, so it appears pixelated when shown on the stream.

