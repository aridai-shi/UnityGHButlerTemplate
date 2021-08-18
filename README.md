
# UnityGHButlerTemplate

A 2D template with a workflow that exports releases to itch.io. Follow this configuration guide to get a project up and running with the capability to push changes to itch in no time flat!
## 1. Get your Unity license!
To be able to build Unity games remotely, we'll need to give this repository a Unity license, so that Github is allowed to build the game.
Run the ``Acquire activation file`` workflow on GH Actions manually and look in the artifacts for ``Unity_v2020.3.16f.alf`` or a simmilar file with a .alf extension (if you're a proffessional/commercial user, you might have to modify the workflow in ``.github/workflows/activate.yaml`` to get the pro license). Sign into your Unity ID at [license.unity3d.com](https://license.unity3d.com/manual), upload the .alf file there and fill out your license details. You'll recieve a .ulf file, that's the license file we need. Open  `GitHub`  >  `Your Repository`  >  `Settings`  >  `Secrets`, create a secret called  `UNITY_LICENSE`  and add the contents of the obtained license file (`.ulf`). Yes, add the entire XML contents to the GitHub secret.
## 2. Get butler activated!
Butler is the api that itch.io uses to let programmers interact with the platform and what we're gonna use to send complete builds to the game.
First things first, create a new game on itch.io (to do this you'll need an account - create one if you haven't yet). Then, go to your account's settings, navigate to ``API keys`` (type in your password if needed) and hit ``Generate new API key``. You should see a new entry in the list of keys - hit ``View`` next to it and copy it. **[DON'T SHARE THIS WITH ANYONE, THIS CAN BE USED TO DO SERIOUS DAMAGE TO YOUR ITCH ACCOUNT IF IT GETS LEAKED ONLINE.]** 
Instead, create a new secret (`GitHub`  >  `Your Repository`  >  `Settings`  >  `Secrets`) called ``BUTLER_CREDENTIALS`` and paste the key there. Now, even if you let other people access the source, noone will be able to get the key without going to your itch settings.
**[SHOULD THE KEY GET LEAKED, GO TO THE API KEY SETTINGS IN ITCH AND PRESS** ``Revoke`` **NEXT TO IT AS SOON AS POSSIBLE, THEN REPEAT THE PROCESS WITH A NEW KEY. WHEN A KEY IS REVOKED, IT CAN NO LONGER BE USED TO AUTHORIZE ACCESS TO YOUR ITCH ACCOUNT.]**
## 3. Fill in your game's details!
This is the simplest step. Add 2 secrets and fill them in as follows
``ITCH_GAME`` > The name of the game in itch.io
``ITCH_USER`` > Your username in itch.io
For example, if I wanted to upload the game to aridai.itch.io/spirit, I'd set ``ITCH_GAME`` to ``spirit`` and ``ITCH_USER`` to ``aridai``.
## 4. Push your first release!
Whenever you feel like making a version of the game available to your beta testers/the public/anyone who can visit the game's itch.io page, you can push a commit to the ``release`` branch (if it's not there, create it) and, provided you did the previous steps correctly, Github will build your game for Windows, Mac and Linux (and Android and WebGL if you fiddle with the settings in ``itch.yml``) and export it to itch.io.

### Have fun making your games just a bit faster!