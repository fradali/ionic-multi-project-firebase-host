# How to create and config project

# 1- Create a workspace

ng new yourOwndirectory --createApplication=false
cd ./yourOwndirectory
 
# 2- Create our projects directory

mkdir projects

# 3- Add ionic.config.json to root Project

 fill it with : 
 ```
{
  "projects": {}
  } 
```
  
# 4- Create two ionic projects

cd ./projects
ionic start appOne blank
ionic start appTwo tabs

# 5- Avoid Configuration problems 

Now you have a projects folder with 2 Ionic projects, a good start so far. If you were to follow the official guide, it wouldn’t work yet as the projects would not be found.

The reason is that the automatically generated angular.json file contains a generic app keyword, and we have to change it to match the name of our projects.

We need to change every angular.json :

  -- "defaultProject": "appOne"
  -- "projects": {  ->"appOne": {
  -- replace every app: by your name  which should be another 12 occurrences in the whole file.

  A final look at the root ionic.config.json shows that the apps were added:
  
 ```
{
  "projects": {
    "appOne": {
      "name": "appOne",
      "integrations": {},
      "type": "angular",
      "root": "projects/appOne"
    },
    "appTwo": {
      "name": "app",
      "integrations": {},
      "type": "angular",
      "root": "projects/appTwo"
    }
  }
}
```

# 6- Creating our Pwa 
Follow this link : https://ionicframework.com/docs/angular/pwa for every project (DO NOT DEPLOY TO FIREBASE)

# 7- Multi hosting Firebase

 1. install firebse tools : npm install -g firebase-tools
 2. cd root project
 3. run this cmd : firebase init hosting
 4. Now we just need to update the firebase.json hosting config. Each site has a target that points to the public deployable code in the www folder. ( Array of hosting object : duplicate the example in this url https://ionicframework.com/docs/angular/pwa#firebase and set a target for each application)
 5. Define Hosting Targets : 
 For this just run this cmd : firebase target:apply hosting 'appName' 'Name in firebase' (run it X times for X project)

# Firebase Deployment

Our configuration is complete. We can deploy all sites together with:

firebase deploy --only hosting
Or deploy a single site based on the target name:

firebase serve --only hosting:appOne

# More infos && useful links

This Tutorial is base on two other ones, you can check them :

- https://devdactic.com/ionic-multi-app-shared-library/
- https://fireship.io/lessons/deploy-multiple-sites-to-firebase-hosting/

Other links you may need:
- https://ionicframework.com/docs/angular/pwa#firebase
- https://ionicframework.com/docs/cli/configuration#multi-app-projects
- https://www.youtube.com/watch?v=mlCdfAvny6o
- https://www.youtube.com/watch?v=NrkFBmBFA6k




