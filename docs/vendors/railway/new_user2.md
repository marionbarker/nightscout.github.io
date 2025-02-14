# Railway Nightscout

Method 2: using the help page

<span style="font-size:smaller;">**APPLIES TO:**</span> <img src="../../img/railway-app-logo.png" style="zoom:80%;" />

</br>

!!!info "Too complicated? Not what you're looking for? Consider a hosted Nightscout service! Check for easier solutions [here](../../../#nightscout-as-a-service)."  
<span style="font-size:larger;">Interested in building a Nightscout DIY site?  Make sure you **read and understand [this](/#how-much-does-it-cost)** before starting.</span>

</br>

**Pros**:  

> The developer plan allows you to run Nightscout [for free](https://docs.railway.app/reference/plans#developer-plan-offering)  
> Migration process is really simple  
> You can use a local Mongo database, cost is $0.000231 / GB / Minute  
> The developer [plan](https://docs.railway.app/reference/plans) is meant for hobbyist workloads  

**Cons**:  

>Using the M0 [MongoDB Atlas](../../mongodb/atlas/) database  
>Railway network model generates missing data issues with some follower apps and devices

</br>

## Set up a new Nightscout

### Create your Railway and GitHub accounts from a computer.

!!!note  
    Do not change device/computer/browser during the setup process!  
    If you have unexpected issues when creating your site, restart with another browser.

</br>

### Step 1: Create a GitHub account and fork `cgm-remote-monitor`

</br>

If you don't have a GitHub account follow [**this link**](../../../nightscout/github/#create-a-github-account) to create one and come back.

Follow this link [**this link**](../../../nightscout/github/#fork-the-nightscout-project) to fork the Nightscout `cgm-remote-monitor` project into GitHub, once done proceed to step 2 below.

</br>

### Step 2: Create a Railway account

a) Open [Railway](https://railway.app) in a new browser tab and click `login`. Login with GitHub.

<img src="../img/Railway00.png" style="zoom:80%;" />

<img src="../img/Railway01.png" style="zoom:80%;" />

</br>

b) If the following screen shows-up, select `Authorize Railway App`.

<img src="../img/Railway02.png" style="zoom:80%;" />

</br>

c) Click on `Please agree to the new terms to keep on using Railway`.

<img src="../img/Railway03.png" style="zoom:80%;" />

</br>

d) Scroll down and click `I agree with Railway's Terms of Service`.

<img src="../img/Railway04.png" style="zoom:60%;" />

</br>

e) Scroll down and click `I will not deploy any of that`.

<img src="../img/Railway05.png" style="zoom:60%;" />

</br>

f) You should now see this. You've created your Railway account.  
If it still shows 200 hours, refresh your browser page.

<img src="../img/Railway06a.png" style="zoom:80%;" />

</br>

g) You need to use Nightscout for more than 500 hours per month: upgrade your account to a Developer plan. Click on the `Starter Plan` information and select `Remove Resource Limits`.

<img src="../img/Railway06b.png" style="zoom:80%;" />

</br>

Enter your credit card information and select `Subscribe to a Developer Plan`.

<img src="../img/Railway06c.png" style="zoom:80%;" />

Your card will be billed 1$ that will be refund immediately. Bank fees won't be refund.

</br>

!!!note "One-off purchase"  
    <img src="../img/Railway06d.png" style="zoom:80%;" />  
    <img src="../img/Railway06e.png" style="zoom:80%;" />  
    If you are reluctant to leave a billing method to Railway, you can **opt for a one-off 5$ purchase guaranteeing you access to a Developer plan** until this credit will be used (which is also an insurance against seeing your site stop unexpectedly).  
    No billing will occur after the initial credits are fully used. They will transfer month to month with no known limit in time.

</br>

### Step 3: Create your database

- #### You can reuse your existing MongDB Atlas database.    

Migrating from Heroku? [Edit your Heroku site variables](../../heroku/new_user#editing-config-vars-in-heroku) and copy the `MONGODB_URI` or `MONGO_CONNECTION` variable.  
    Lost your string? [Recover it](../../../troubleshoot/atlas/#recover-your-connection-string) from MongoDB Atlas.

- #### You can create a new MongoDB Atlas database.

To create a new MongoDB database follow [these instructions](../../mongodb/atlas/#create-an-atlas-database) and come back with your `MONGODB_URI` connection string.  
The Atlas database size is limited to 512MiB of data and is free to try. This might evolve in the future.  
When the MongoDB Atlas database is full your Nightscout site will crash.

- #### You can create a new Railway Mongo database.

!!!warning "Costs"  
    Adding a Railway Mongo database will not fit forever in 5$ per month.  
    If you don't keep its dimension very small (<200MB) you will most probably be charged for it: the cost is $0.000231 / GB / Minute  
    A good database is important for your Nightscout site reliability.

a) Click `New Project` from your Dashboard screen (top right).

<img src="../../../vendors/railway/img/RailwayDB01.png" style="zoom:80%;" />

</br>

b) Click  `Provision MongoDB`

<img src="../../../vendors/railway/img/RailwayDB02.png" style="zoom:80%;" />

</br>

c) Select your new MongoDB project.

<img src="../../../vendors/railway/img/RailwayDB03.png" style="zoom:80%;" />

</br>

d) Go to the `Connect` page.

<img src="../../../vendors/railway/img/RailwayDB04.png" style="zoom:80%;" />

</br>

e) Move the mouse to the end of the line showing the `Mongo Connection URL` and click the copy icon.

<img src="../../../vendors/railway/img/RailwayDB05.png" style="zoom:80%;" />

</br>

!!!warning "This is an important information"

Now that you have **copied** the resulting `MONGODB_URI` string, keep it in a **safe place**, you will need it later.

</br>

## Step 4 - Deploy Nightscout in Railway

a) Click on `Create a New project`.

<img src="../img/Railway06.png" style="zoom:80%;" />

If you don't see that, top right, click `+ New Project`.

<img src="../img/RailwayDB01.png" style="zoom:80%;" />

</br>

b) Select `Deploy from GitHub repo`.

<img src="../img/RailwayM19.png" style="zoom:80%;" />

</br>

c) Select `Configure GitHub App`.

<img src="../img/RailwayM02.png" style="zoom:80%;" />

</br>

d) Choose `Only select repositories`, in the `Select repositories` drop-down select your own fork of `cgm-remote-monitor`.  
Then, at the bottom, click `Install & Authorize`.

<img src="../img/Railway08.png" style="zoom:80%;" />

</br>

e) You should be back to `Deploy from GitHub repo`, select it.

<img src="../img/RailwayM19.png" style="zoom:80%;" />

</br>

f) Now you can select your own GitHub repository.

<img src="../img/RailwayM03.png" style="zoom:80%;" />

</br>

g) Select `Add variables`.

<img src="../img/RailwayM20.png" style="zoom:80%;" />

</br>

h) The Nightscout project will deploy in the background, just ignore it: now we need to setup our Nightscout variables.  
Click on `Raw Editor`.

<img src="../img/RailwayM21b.png" style="zoom:80%;" />

The raw editor will open, leave it like this for now.

<img src="../img/RailwayM21c.png" style="zoom:80%;" />

</br>

i) Open the [**helper page**](../NightscoutVariablesRailway.html) in a new browser tab.

File all necessary fields, click on the Validate button at the bottom of the form, if no error is seen you will have all variables displayed in the text box at the bottom, click on the Copy All button.

<img src="../img/Railway42.png" style="zoom:80%;" />

</br>

j)  Return to the Railway Raw editor. Paste the result. Click `Update Variables`.

<img src="../img/Railway43.png" style="zoom:80%;" />

Your site will redeploy, wait until redeploy completes.

</br>

Congratulations. You created your new Nightscout site with Railway.

Click the site name to open Nightscout.

<img src="../img/RailwayM14.png" style="zoom:80%;" />

</br>

!!!info "Change Railway site name"  
    You should [change your Railway site name](#change-your-railway-nightscout-site-name) now in order to make it easier to remember. **Recommended**.  
    You can also do this later, before setting your uploaders.

</br>

k) Your Nightscout site should open and direct you to a new profile creation.

<img src="../../../nightscout/img/NewNS50.png" style="zoom:100%;" />

</br>

l) Setup your `Time zone` and eventually all other fields. Do not leave any fields empty. If you don't know which value to use, just use the default value. You can change these values later at any time.

<img src="../../../nightscout/img/NewNS44.png" style="zoom:80%;" />

</br>

m) Browse down to `Authentication status` and click `Authenticate`. Enter your API secret. Click `Update`.

<img src="../../../nightscout/img/NewNS45.png" style="zoom:80%;" />

</br>

n) Click `Save`.

<img src="../../../nightscout/img/NewNS46.png" style="zoom:80%;" />

</br>

o) If the following pop-up shows up click `OK`, and check status (upper right of the window).

<img src="../../../nightscout/img/NewNS47.png" style="zoom:80%;" />

</br>

p) If you need to modify your profile after this, authenticate with the lock icon (top right of the page): enter your API secret. Then click on the hamburger menu and select `Profile Editor`.

<img src="../../../nightscout/img/NewNS43.png" style="zoom:80%;" />

</br>

!!!warning "Privacy warning"
    Anyone with access to the URL of your Nightscout site, can view your BG and run reports of your data. It it strongly recommended that you enable [security](../../../nightscout/security) to your site once you're done with the setup.  

</br>

q) Dexcom Share users should see data flowing in after some minutes.
xDrip+ users (including Medtronic [CareLink followers](../../../uploader/uploaders/#medtronic)) should setup the uploader as shown [**here**](../../../uploader/setup/#xdrip).
xDrip4iOS users [here](https://xdrip4ios.readthedocs.io/en/latest/connect/cgm/#nightscout-upload).
[AAPS](https://androidaps.readthedocs.io/en/latest/Configuration/Preferences.html#nsclient) and [Loop](https://loopkit.github.io/loopdocs/operation/loop-settings/services/): consult the relative documentation.

<img src="../../../nightscout/img/NewNS48.png" style="zoom:80%;" />

</br>

</br>

## Change your Railway Nightscout site name

Railways automatically makes a name when creating your new site. It is rather difficult to remember.

You can change the site name but need to keep the `.up.railway.app` domain.

1. Select your Nightscout app

2. Go in `Settings`

3. In `Domains` go to the end of line and click the edit icon

4. Write your new name and check it's available

   Click `Update`

   Your Nightscout URL will now be `https://`*yoursitename*`.up.railway.app`

<img src="../img/Railway38.png" style="zoom:80%;" />

</br>

Change all your [uploaders](../../../uploader/setup/) and [follower](../../../nightscout/downloaders/) devices to reflect the new URL once verified correct functioning of your Nightscout site.

</br>

------

You have completed a new Nightscout site creation. The following section provides more information for database migration and variables edition that you might not need to use now.

------

</br>

## Migrate your MongoDB Atlas database to Railway

!!!warning "Not an easy operation"  
    This is not an easy operation and requires command line instructions using a computer.  
    You can have a trusted person help you perform it, if you can provide both MongoDB Atlas and Railway MongoDB connection strings.

a) Dump your Atlas database

- Follow [these instructions](../../mongodb/atlas/#backup-your-database).

- Make sure you renamed your exported database folder to `test` as this is the default database name in Railway.

b) Copy your Railway database connection string

1. Select your MongoDB database
2. Click on `Connect`
3. Click on the Copy icon

<img src="../../mongodb/img/AtlasX05.png" style="zoom:80%;" />

c) Rename the database dump folder (example for Windows below) to `test` (default)

<img src="../../mongodb/img/AtlasX07.png" style="zoom:80%;" />

</br>

d) Import your Atlas database in Railway

- Open a command line utility (CMD, Terminal, ...) and make your way to the utility folder (if you don't want to include it in your system path). For example in Windows 64bits it's in `C:\Program Files\MongoDB\Tools\100\bin`.

Type a new command starting with: `mongorestore --uri` followed by the database string you copied above in **b)3.**, run it.

<img src="../../mongodb/img/AtlasX06.png" style="zoom:80%;" />

e) Wait until the import completes. You will see a line like this before returning to the command prompt.

```
2022-09-11T09:49:35.331+0200    456003 document(s) restored successfully. 0 document(s) failed to restore.
```

The number of documents will be different but the rest should be identical.

You have completed database restore.

</br>

If you're migrating your database, make sure to [update](#editing-variables-in-railway) the `MONGODB_URI` variable string to the new URI as copied in **b)3.**.  
Refresh your Nightscout browser once deployment completes view to verify data has been imported correctly.

</br>

------

</br>

## Editing Variables in Railway

</br>

#### Method 1 - Web interface

This is recommended when you only need to edit or add few variables.

a) Open [Railway](https://railway.app) and click `login`. Login with GitHub.

<img src="../img/Railway00.png" style="zoom:80%;" />

<img src="../img/Railway01.png" style="zoom:80%;" />

</br>

b) Select your Nightscout project.

<img src="../img/RailwayM15.png" style="zoom:80%;" />

</br>

c) Select your web app.

<img src="../img/RailwayM16.png" style="zoom:80%;" />

</br>

d) Click on `Variables`.

<img src="../img/RailwayM17.png" style="zoom:80%;" />

</br>

e) You can perform various operations on your variables:

1. Add a new variable with `+ New Variable`
2. View the variable value with `Show Value`
3. Edit or delete the variable or its value with the line end menu

<img src="../img/RailwayM18.png" style="zoom:80%;" />

</br>

Note that each variable modification will redeploy your project.

</br>

#### Method 2 - Raw Editor

This is recommended when you must perform lots of changes to avoid multiple project redeploys.

a) Open [Railway](https://railway.app) and click `login`. Login with GitHub.

<img src="../img/Railway00.png" style="zoom:80%;" />

<img src="../img/Railway01.png" style="zoom:80%;" />

</br>

b) Select your Nightscout project.

<img src="../img/RailwayM15.png" style="zoom:80%;" />

</br>

c) Select your web app.

<img src="../img/RailwayM16.png" style="zoom:80%;" />

</br>

d) Click on `Variables`.

<img src="../img/RailwayM17.png" style="zoom:80%;" />

</br>

e) Click on `RAW Editor` top right

<img src="../img/Railway39.png" style="zoom:80%;" />

</br>

f) You can access all your variables in a text editor, each line contains the variable name, the sign `=` then its corresponding value.

`VARIABLE=value`

Perform all your changes taking care of uppercase and lowercase information and click `Update Variables` when finished.

<img src="../img/Railway40.png" style="zoom:80%;" />

</br>

Once saved your project will redeploy.  
If deploy fails, check your modifications...

</br>
