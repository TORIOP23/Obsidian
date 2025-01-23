- Nền tảng backend-as-a-service (BaaS)
- [[Firestore]] là 1 dịch vụ cơ sở dữ liệu thời gian thực của Firebase

## Hosting
- Hosting single page application
- Maximum 36 site per project
- Install firebase cli
```c++ 
firebase init hosting // Deploy to live & preview channels via GitHub pull requests 
firebase init hosting:github // emulate Hosting and your backend project resources at a locally hosted URL. 
firebase emulators:start // view and share your changes at a temporary preview URL 
firebase hosting:channel:deploy CHANNEL_ID 

// deploy 
//// option 1: clone from preview channel 
firebase hosting:clone SOURCE_SITE_ID:SOURCE_CHANNEL_ID TARGET_SITE_ID:live 
//// option 2: Deploy from local project 
firebase deploy only hosting -m "Comment" 

// create site 
firebase hosting:sites:create SITE_ID 
// delete site 
firebase hosting:sites:delete SITE_ID 

// hosting target .. 
/// RESOURCE_IDENTIFIER: SITE_ID 
/// TARGET_NAME just a unique name 
firebase target:apply hosting TARGET_NAME RESOURCE_IDENTIFIER 
firebase emulators:start --only hosting:TARGET_NAME 
firebase hosting:channel:deploy CHANNEL_ID --only TARGET_NAME 
firebase deploy --only hosting:TARGET_NAME
```