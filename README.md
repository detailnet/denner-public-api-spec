# denner-postman
[Postman Collection](https://www.getpostman.com/) for Denner 2.0 Portal and Web Services.

## How to use it
Following guide applies for:

- [Postman REST client (Packaged App)](https://www.getpostman.com/)
- [Postman REST client (Chrome extension)](https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm)

### Initial setup
 
- Remove collection if already present ([see note below](#initial-setup-note)).
- Import collection:
  - Select "Collections" tab (left menu), click on "Import into Postman" icon.
  - Choose tab "Download from link".
  - Enter collection link ([choose from section below](#collection-data)).
  - Click on "Import" button (once only).
- [Setup/Import environments](#import-environments).
- [Setup global variables](#setup-global-variables) (For the moment needed only for production environments).
- Choose an environment.
- Run requests.

> <a name="initial-setup-note"></a>Important: If you already have the collection into your Postman application, you should first remove it before import.
> If not, the latest collection (copy) you import will change all collection reference UUID's, making the future commit/merge unreadable.

#### Collection data

Choose the one that best fits the testing situation you need:

- Main GitHub repository | https://raw.githubusercontent.com/detailnet/denner-postman/master/collections/default.json
- Own GitHub fork | https://raw.githubusercontent.com/{own-git-user}/denner-postman/master/collections/default.json
- Local checkout through Protobox | http://denner-postman.collections.web01.detailnet.me/default.json

> You can also access different branches on GitHub (replace `master` with the branch name).

#### Import environments

- Go to the environments manager window.
  - Move the mouse pointer over the eye dropdown menu (top bar).
  - Click on "Manage environments"
- Click on "Import" button, choose all files in the project environments directory (all at once).

> There is no direct possibility to import from an URL, but you can use your OS as wrapper. 
> To do so enter an URL instead of a file in the file selection window (e.g.: https://raw.githubusercontent.com/detailnet/denner-postman/master/environments/development.json).

#### Setup global variables

We use global variables to store data that is your own, and must not be shared with others.

Currently we support following global variables:

- `denner_advertising_app_id`
- `denner_advertising_app_key`
- `denner_appraisals_app_key` (doesn't require an "id")
- `denner_articles_app_id`
- `denner_articles_app_key`
- `denner_assets_app_id`
- `denner_assets_app_key`
- `denner_banners_app_key` (doesn't require an "id")
- `denner_stores_app_id`
- `denner_stores_app_key`

Set up global variables:

- Go to the environments manager window.
  - Move the mouse pointer over the eye drop-down menu (top bar).
  - Click on "Manage environments".
- Click on "Globals" button.
- Add the variables.

### Save tool changes back to project/repository

- Move your mouse pointer over the collection name (left menu), click on "Share collection" icon.
- Click on "Download" button.
- Overwrite your local repository's [collections/denner-api.json](collections/denner-api.json) file.
- Review changes with your preferred editor:
  - Replace tabs with 4 whitespaces.
  - Reset owner to original.
  - Commit only modified/added routes through Git.
