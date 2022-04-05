---
title: Changelog
description: ""
position: 2
category: ""
---

## 3.0.1

> 2017/10/15

### Bug Fixes

- **account:** calling setRoot at end of login process, also fixed persistence of account photo after upload
- **chat:** fixed storage call
- **firebase:** add polyfill
- **session:** switch online/offline states
- **tasks:** fixed storage call
- **tasks-list:** improve duration time of loader

### Features

- **config:** allow navigation

## 3.0.0

> Releasing the 1x1 chat feature

- refact: now Firetask relies its own module with features by folder-type eg: `modules/firetask/feature`
- refact: rename pages to prefix ft-name-page
- docs: style bg in shared-variables on variables.scss
- refact: added prefix `ft` of `Firetask` in all features (pages, components, providers, etc) to avoid code name collision and improve code reusability
- refact: renamed provider user to session as it make more sense
- refact: pluralize config folder name
- refact: changes type of all configuration files from `json` to `ts`
- refact: rename `setup` provider to `utils`
- fix: improve speed load of first screen after login
- fix: removed a lot of setTimeout
- fix: improve first load when user is already logged
- refact: back all configuration files to pure typescript instead of json
- fix: removed a lot of unnecessary promises
- fix: removed count transactions as it can be achieved with a simple firebase query
- refact: removed `onAuthStateChanged` event in favor of using localStorage to check if user has session
- fix: removed a lot of ionic events in favor of a pattern using only angular providers

## 2.1.0

> Pre releasing chat feature

- fix(photo-manager): picFromCamera was working with full image quality, what was causing low upload speed
- feat(photo-manager): added a progress bar to indicate upload status
- refact(user/provider): profileSync method renamed to just sync
- chore(accounting): merge with sync method. now there is no need to use accounting method anymore
- refact(database): changes path of user profile data, now its on the root of object to facilitate searching data, (eg: email address) for the database query search
- refact(user/provider): profile method renamed to current
- feat(friends): added the friends list feature. a friend can be added through user email address
- feat(chat): added the chat feature
- fix(logout): clearing all storage data
- refact(): renamed stuff module to setup
- feat(setup/provider): added a provider to wrap some common helpers
- chore(): updates to ionic-angular 3.2.1

### Firebase Rules

Replace your current setup to

```js
"users": {
    ".write": "auth.uid != null",
    ".read": "auth.uid != null",
    ".indexOn": [
        "email"
    ]
}
```

Add the chat permissions

```js
"chat": {
    ".write": "auth.uid != null",
    ".read": "auth.uid != null",
    ".indexOn": [
        "from",
        "to"
    ]
}
```

## 2.0.5

full rewrite from scratch to meets the latest changes and features of Angular and Ionic

## 1.1.0

> 02/15/2017

In this version we finally was able to add new features on profile page, now you'll can change the profile picture by taking a photo from your camera, crop it or just select another image from device library. Check out bellow the full log:

### Requirements

- Update your ionic and cordova globally `-g`
- Add the cordova platform with `@latest`
- Make a clean install from zip

### Breaking changes

- Due to the changes on how we load the configuration files across the app, now you do need to first create your [firebase console account](https://console.firebase.google.com/), then copy their web config object, that you can easy obtain through 'authentication' screen on your firebase project, then paste in src/config/firebase.json

### Changes

- [chore] Updates package.json to work with latest dependencies of Angular/Ionic (final release)
- [refact] All the configs (src/config) were replaced with json, since now Typescript finally is supporting importation of .json files out-of-box
- [refact] Component account-avatar property hideDetail now is hideName
- [feature] New behaviors added to User provider for profile photo management
- [feature] New component account-photo-manager to change profile picture and cropping based on camera or selecting an image from device gallery
- [improve] account-avatar to work with base64 images and some other fixes
- [fix] google login to work with the latest ionic version
- [fix] slides issues due to migration for the latest ionic version
- [fix] error on importing asset font ‘marmelad’
- [feat] adds ‘trash’ button on task detail to delete it. The default behavior (drag to left on listing) does remain the same.
- [fix] logout. Now when user click menu > logout it first does get the current nav instance and send user to tutorial screen through setRoot, only then the other stuff are being called.

> Note: in dev mode (without --prod flag) the console are displaying a warning. Not a serious problem but we're keeping an eye on it

- [chore] update app-header component to ionic 2 final
- [fix] delay on clicking in the right side nav-options button (app/header), also changes the ion icon to "options", it make more sense and have a more "clickable" area
- [refact] account-avatar: removes robohash because it was generating issues on ionic —prod versions. Instead and also to make more sense we added a default user-blank image for new accounts (src/assets/img/user-blank.svg)

## 1.0.0

12/18/2016

Christmas coming and Santa Claus arrived early. In this version we finally get to number 1. All code has been refactored and tested on Android (4.4/6.1) and iOS (10).

From now on we can grow our product without many problems.

### Requirements

- Update your Ionic and Cordova `-g`
- Add the cordova platform with `@latest`
- Make a clean install from zip

### Changelog

- Removed all unnecessary setTimeout() calls
- Removed all logic from the pages
- Splits all features (logic, html, scss) into components to easy locate/change/reuse
- Cleans the code and add a bit more inline docs
- Fixes some critical bugs
- Fixes the issue where some times the view were not updating. Solution: NgZone to async calls
- New `Task` Provider
- Removes logic about tasks from `User` Provider
- Removes `.config` from config file names
- Migrates to Ionic RC4 and `app-scripts` 0.0.47
- Refacts user to make logout method be internal and not static
- Adds Admob provider to abstract the logic from app component
- Cleans app component moving some methods to User provider
- Adds firebase provider with method to instantiate it, removing the initialization from user provider. So now Firebase can be easy injected anywhere
- Changes User.logout() from static to public. So now it needs to be passed into constructor()
- Adds new component `app-header`
- Adds new component `app-header-popover` removing the logic from pages
- Adds new component `tasks` with all the logic embedded
- Removes pages `task-list` and `task` in favor of having a `home` that calls the `tasks` component
- Adds a loading image to `tasks` component
- Cleans the logs a bit
- Improves the about page using ionic list
- Added tutorial page to menu
- New splash screen with .psd
- Added new component `app-menu` removing all logic from `app.component`
- Removes unnecessary imports

## 0.3.0

- docs fixed and improved
- account-password: design improvement
- account-email: design improvement
- account-name: design improvement
- account-forgot: design improvement
- account-signup: design improvement
- account-login: design improvement
- account-forgot: fixed the validation problem
- account-signin: fixed the login retry issue #9

## 0.2.2

- add stats feature to counting total of users and tasks

## 0.2.0

- upgraded to Ionic RC3
- fixed iOS and WP platform issues
- fixed account-login issues
- fixed account-forgot issues
- fixed account-signup issues
- fixed menu issues
- fixed task detail issues
- fixed profile issues

## 0.1.2

- New feature: setting user device token to send individual push notifications

## 0.1.1

- Fix Google Services

## 0.1.0

- General fixes
- Migration to Ionic2 RC1
- New feature: Add native AdMob plugin
- New feature: Add native Firebase plugin to enable analytics, push notifications, event tracking, crash reporting and more from Google Firebase

## 0.0.2

- General fixes
- New feature: Add native share plugin
- New feature: Add native app version plugin
- New feature: Full offline support

## 0.0.1

Launched Firetask with features

- Tutorial
- About
- Account Login
- Account Login Social
- Account name change
- Account email change
- Account forgot password
- Account signup
- Task
- Task List
- Task Edit
- Task Remove
