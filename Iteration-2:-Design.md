# Groovy Piano
### Group 12: 
Nav Thakur, Heather Han, Gianluca Croso, Lucas Winch, Eric Walker  

***
## Table of Contents
* [Vision Statement](#vision-statement)
* [Feature List](#feature-list)  
* [Domain Analysis](#domain-analysis)
* [UI Sketches](#ui-sketches)
* [Use Cases](#use-cases)
    * [Upload Sheet Music](#upload-sheet-music)
    * [Upload MP3](#upload-mp3)
    * [Annotate Sheet Music](#annotate-sheet-music)
    * [Listen to Auto-Generated Song](#listen-to-auto-generated-song)
    * [Play Along to Sheet Music](#play-along-to-sheet-music)
    * [Play Along to Music](#play-along-to-music-optional)
    * [Compare MP3 to Music Sheet](#compare-mp3-to-music-sheet)
* [Interfaces](#interfaces)
* [Class Diagram](#class-diagram)
* [Architecture](#architecture)
* [Initial Code](#initial-code)

## Vision Statement
Groovy Piano is a web application that facilitates playing music. The application provides a web-based interface that allows users to upload, view, and track sheet music as they play. When playing music, the application eliminates the need for users to physically move the pages themselves, and instead allows for automated music sheet scrolling based on a user-defined tempo. This is particularly useful as users will no longer have to pause while playing and interrupt the song. Additionally, our application allows users to record or upload soundtracks of themselves playing music. To help users improve and identify their mistakes, the application can generate sound from the sheet music. The recordings and the generated music can then be used in our side-by-side comparison interface with sheet music to help users identify their mistakes.

## Feature List

* Account
    * User has a profile/account containing their uploaded sheet music and their playing data
    * User can log-in to their account
    * User account can be connected to Facebook
    * Users can view sheet music associated with their account
* Import Data
    * Users can upload their own mp3 audio to their account
    * User can associate mp3 audio files to specific sheets
    * &#x1F536; [Extended Feature] User can record their own music
    * Users can upload sheet music as images to application
    * Sheet music image can be converted to MIDI
    * Data is automatically organized by upload date
* Music Display
    * Sheet music is displayed on screen with adjustable size
    * Users can set tempo for progression along the sheet music as they play
    * Progression can be paused
    * The sheet music can be converted to sound
    * Service can play individual measures of the sheet music separately
    * Users can annotate sheet music
    * &#x1F536; [Extended Feature] Users can write comments on sheet music
* Music Analysis
    * User can compare their own music playing to the music derived from sheet
    * User mp3 is shown on right side of screen and sheet music is displayed on left side
    * &#x1F536; [Extended Feature] The sound signals are compared to check for issues with the user's pace, notes, etc  
    * &#x1F536; [Extended Feature] Service displays errors made by user on sheet music to improve user's ability to play the music
    * &#x1F536; [Extended Feature] Detect tempo on an audio track.
    * &#x1F536; [Extended Feature] change speed of playback and add metronome to let the user play along.

## Domain Analysis
Main entities within application:
* User Account:  
The user account is the entity that identifies an user and what data he has access to. It contains uniquely identifying information for the user as well as a list of songs the user has data for. The following are the main components of a user account:
    * Username
    * Password
    * Email
    * Song List (Sheets and/or Recordings)
* Song:  
A song is the entity responsible for associating all the information the user has related to each individual piece of music. It is uniquely identified by the title and author. The user can optionally associate a default tempo value that will be used to track the sheet. The following are the main components:
    * Song title
    * Author
    * Default Tempo
    * Sheet Music
    * Recording List
* Sheet Music:  
Sheet music contains all the information needed for the user to play a song, track it at a specific tempo and listen to auto-generated sound for the entire song or specific measures. It is uploaded as an image or pdf and converted into a model that represents the song.
* Music Recording:  
MP3 recordings the user wants to associate to a specific song in order to track his progress, have examples or compare to the auto-generated sound from the sheet music. Includes the components:
    * MP3 file
    * date/time recorded 

## UI Sketches
### User portal with list of uploaded songs
<img src="https://github.com/jhu-oose/2017-group-12/blob/master/UI_sketches/Profile.png" >

### Mechanism to upload new sheet music
<img src="https://github.com/jhu-oose/2017-group-12/blob/master/UI_sketches/Upload Sheet Music.png" >

### Mechanism to upload new recordings
<img src="https://github.com/jhu-oose/2017-group-12/blob/master/UI_sketches/Upload Recordings.png" >

### Sheet music view with song tracking and ability to auto-generate matching sound
<img src="https://github.com/jhu-oose/2017-group-12/blob/master/UI_sketches/Play.png" >

### Comparison view for comparing recorded versions with auto-generated sound and sheet
<img src="https://github.com/jhu-oose/2017-group-12/blob/master/UI_sketches/Side-by-side.png" >

## Use Cases

### Upload Sheet Music
1. User logs into profile
2. User selects "Upload Sheet" option
3. User specifies song title
    * User optionally specifies author
4. User searches for sheet image to select
5. User selects image or pdf to upload
    * If incorrect format, user must select new image
    * If unable to read/convert image to MIDI, user must select new image
6. Image is converted to MIDI and displayed to user
    * User can optionally connect MIDI file to an already uploaded recording using the dropdown selection button
### Upload MP3
1. User logs into profile
2. User selects "Upload MP3" option
3. User specifies song title
    * User optionally specifies artist
4. User searches for music file to select
5. User selects mp3 file to upload
    * If incorrect file format, user must select new file
    * If unable to read file, user must select new file
6. File is shown as uploaded
    * User can optionally connect mp3 file to an already uploaded sheet using the dropdown selection button
### Annotate Sheet Music
1. User logs into profile
2. User selects sheet to play
3. User selects option to annotate sheet
4. User selects measure to annotate
5. User can mark location with meaningful symbol
6. &#x1F536; [Extended Feature] User adds comment at location by selecting symbol
7. User saves annotations
### Listen to Auto-Generated Song
1. User logs into profile
2. User selects sheet to play
3. Optionally, user selects start and end point from the sheet to be played (otherwise entire song will be played)
4. User sets sound output ON
5. User clicks play button and listens to auto-generated song
### Play Along to Sheet Music
1. User logs into profile
2. User selects sheet to play
3. If there is no default tempo associated to the song, or if user wants to change it, user enters tempo in bpm
4. Optionally, user checks checkbox to turn on metronome
5. User clicks play button to start moving along sheet music
### Play Along to Music [Extended Feature]
1. User logs into profile
2. User selects recording to play
3. prompt user to estimate the tempo by tapping keyboard button along to the reccording
4. tempo and start time of the metronome are calculated and associated with the mp3. 
5. the user can press the play button to the music, slider to change the tempo, checkbox to mute the metronome.
### Compare MP3 to Music Sheet
1. User selects music analysis option
2. User selects music sheet and corresponding audio file
3. User can see audio file information on right side of screen, and sheet music on left
4. User can compare audio file to sheet music by measures and check if music was played correctly

## Interfaces

*Full API documentation written using Swagger following TA suggestion.

*API_docs directory includes YAML/JSON as well as index.html which can be downloaded to view the full documentation in a browser.

*Documentation can be seen at https://giancroso.github.io

## Class Diagram
![](https://github.com/jhu-oose/2017-group-12/blob/master/UML%20Sketch/Groove.png)
## Architecture
We use a MicroServices Architecture.
### Client Side
* Our front-end web application will use the Angular2 framework (consisting of HTML, SASS, TypeScript,) which will display the website to our users. This web application will be hosted on AWS, and will send HTTPS requests to our web server which are then forwarded to our backend rest-APIs.

### Server Side
* The backend consists of two Rest-API’s that respond to HTTP requests coming in from the front-end. Each API is built using the Django REST framework to perform RESTful communication. 

* The first one handles account management, so that the client side displays information pertaining to a logged in user. 

* The other service handles the “music engine”, which means it returns/analyzes sheet music and audio. 

* Each API also has its own database to run queries and access data. This is done so that each service (API) does not cripple the other service when there is a failure in the system.

* We use mySQL databases, and the Django ORM will query the database when the API calls for it.


### Planned Libraries
* Optical Music Recognition (ORM) libraries:
    * Audiveris (Current choice)
    * Piano-Poe
    * OverScore
    * SheetVision
    * music21 (support choice)


<img src="https://github.com/jhu-oose/2017-group-12/blob/master/architecturediagram/OOSEArchitectureDiagram - ERD.png" >

## Initial Code

The django framework has been created with two apps, one for the dealing with the accounts and one for the music engine. Some of the login code was started, urls and views were set up, login.html was created, settings were changed so that login.html is loaded upon site startup.