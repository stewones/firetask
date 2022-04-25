---
title: Seed Database
description: ""
position: 10
category: Setup
---

<alert>

This step requires a [Service Account](/setup/firebase-add-service-account) in place

</alert>

From the app root issue these following commands in order

1. `npm run seed:users`
2. `npm run seed:tasks`
3. `npm run seed:boards`

- You can check email+password of created users at `seeds/users.json`
- Check out Firebase console to see data added on Cloud Firestore.
- Once it's completed you should be all set to [run the app](/setup/app-run).
