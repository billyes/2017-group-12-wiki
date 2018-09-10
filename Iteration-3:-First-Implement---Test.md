# Groovy Piano
### Group 12: 
Nav Thakur, Heather Han, Gianluca Croso, Lucas Winch, Eric Walker  

***
## Class Diagram
![](https://github.com/jhu-oose/2017-group-12/blob/master/UML%20Sketch/Groove%20-%20Iteration3.png)
This was changed from iteration 2 to better describe the model and remove architecture specific information such as service and bootstrap classes.

## Code description

### Automated Build
Bash script build added to download and install necessary dependencies and start the service. We assume the user has homebrew, python3 and pip installed. At this point, the build script will at one point ask for the creation of a superuser. Give any username, feel free to leave the email field blank, and create a password. The service will then start and be accessible at localhost:8000, where the created user can be used to log in.

### Accounts app
Full local login loop with authentication for users created using manage.py createsuperuser. No sign up page created yet. Admins can modify profile information using django admin console at localhost:8000/admin (when running server). Relevant models added, each user associated with first name, last name, user location. Song models include a user who owns them.

### Music engine app
Models created for SheetMusic, Song and Recording. ImageProcessor and SoundGenerator classes created. Audiveris tested and integrated to be used as Optical Music Recognition engine by ImageProcessor. Music21 library tested and integrated to process MusicXML in SoundGenerator. Simple unitTests created and can be run using python tests.py within the musicengine directory. This app is not yet integrated with the frontend, and therefore does not yet receive requests.