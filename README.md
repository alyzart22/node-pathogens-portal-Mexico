# node-pathogens-portal

A minimal/example hugo site for node pathogens portal, it uses a [theme](https://github.com/ScilifelabDataCentre/node-pathogens-portal-theme) inspired by [Swedish pathogen portal](https://www.pathogens.se/) and [Swiss pathogen portal](https://pathogensportal.ch/), while following the visual identity of [central pathogens portal](https://www.pathogensportal.org/).

More information about Pathogen Portal Nodes (PPN) and Pathogen Data Network (PDN) can be found in this [Onboarding material](static/docs/Onboarding_Introduction.pdf)

## Content

- [Requirements](#requirements)
- [Setup](#setup)
- [Configuration](#configuration)
  - [Must updated params](#must-updated-params)
  - [Multi language site](#multi-language-site)
- [Customisation](#customisation)
  - [Dashboards](#dashboards)
  - [Highlights](#highlights)
  - [Topics](#topics)
  - [News](#news)
  - [Events](#events)
  - [New content](#new-content)
- [Themes](#themes)
  - [Layout](#layout)
  - [Update theme](#update-theme)
- [Analytics](#analytics)
- [Hosting](#hosting)
- [Credits](#credits)

## Requirements

- `Hugo v0.139` or higher (see [here](https://gohugo.io/installation/) for Hugo installation)

## Setup

The following steps are for a quick setup/starting guide, `Hugo` should have been installed (link mentioned above) in your computer before following the below mentioned steps.

1) Fork this repository to your own github organisation, if desired you can use different name for the repository while forking. More information on how to do that can be found [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) or watch the [demo video](https://youtu.be/v53tevQV-7I).

2) Clone the forked repository to your computer using the following command in a terminal ([demo video](https://youtu.be/671ij1kB2EU))

    ```
    git clone --recursive <your fork url>
    ```

    The `<your fork url>` mentioned above is the github url of your fork. It can be found as mentioned [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo#cloning-your-forked-repository).
    
    **Note** the `--recursive` mentioned in the command is **important to include** in the command.

3) Change into the downloaded repository

    ```
    cd <repository name>
    ```

4) Start `hugo` and see if works as expected ([demo video](https://youtu.be/L4cLXx90dJI))

    ```
    hugo serve
    ```

    If everything is good, you should see output similar to what mentioned below

    ```
    Start building sites … 
    hugo v0.139.3+extended+withdeploy darwin/amd64 BuildDate=2024-11-29T15:36:56Z VendorInfo=brew
    ........
    ........
    Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
    Web Server is available at http://localhost:1313/ (bind address 127.0.0.1) 
    Press Ctrl+C to stop
    ```

5) Open a browser and typr the URL `http://localhost:1313/`. You will see the bare minimum website with example content.

## Configuration

By default, `hugo` looks for the config file named `hugo.yaml` in the root directoy. You can configure the site by editing the config file to your need. Some useful config options are mentioned below and you can read more about `hugo` configuration [here](https://gohugo.io/getting-started/configuration/)

### Must updated params

Site wide variablea can be added as custom parameters. The following parameters **should be added/updated** in the `hugo.yaml`. If the below mentioned vairables already have a _(dummy)_ value set, overwrite it with desired value.

#### Node info

Node related information are set using the following variables in `params` section. These should be set the show your logo beside the pathogens logo at the top of the website.

```yaml
  node_logo: ""
  node_url: ""
  node_country: ""
```

#### Social media info

Node's social media accounts can be highlighted if the following variables are set in the `params` section.

```yaml
  social_media:
    show_in_footer: true
    twitter_url: ""
    linkedin_url: ""
    contact_email: ""
```

When `show_in_footer` is set to `true`, it will add a section `Connect` in the footer with the links to node's social media urls

### Multi language site

Hugo supports multilingual website, read more [here](https://gohugo.io/content-management/multilingual/#configure-languages) about language configuration and [here](https://gohugo.io/content-management/multilingual/) for multi language content.

## Customisation

This section covers how to add and modify your content. All the content should be placed in the `content` folder. Initially, the repository consists of the following type of content.

**NOTE:** The existing content are just sample files to give a demonstration, it should be removed and/or replaced with your own desired content.

### Dashboards

Dashboards are displayed on the main page as cards. The dashboard can be either

- **Internal** - the content and the visualisation are written by you ([example](https://raw.githubusercontent.com/ScilifelabDataCentre/node-pathogens-portal/refs/heads/main/content/dashboards/internal_dash.md))
- **External** - the content file only has front matter with a `redirect_url` ([example](https://raw.githubusercontent.com/ScilifelabDataCentre/node-pathogens-portal/refs/heads/main/content/dashboards/external_dash.md))

To add a new dashboard, run the following command from the repository's root. The `<desired file name>` in the command is the new file you want (but without spaces). 

```
hugo new content dashboards/<desired file name>.md
```

The above command will create a new file in the `content/dashboards` directory. Fill in the front end matter (i.e. the variables at the top of the file and between two `---`) with appropriate value and start writing your content.

### Highlights

Data highlights are like articles highlighting the research (and its data) published by the node country's researchers. To add a new highlight, run the following command from the repository's root. The `<desired file name>` in the command is the new file you want (but without spaces).

```
hugo new content highlights/<desired file name>.md
```

The above command will create a new file in the `content/highlights` directory. Fill in the front end matter (i.e. the variables at the top of the file and between two `---`) with appropriate value and start writing your content.

### Topics

Topics are refined list of categories that you could use to group your contents for faster overview. To add a topic, run the following command from the repository's root. The `<desired file name>` in the command is the new file you want (but without spaces).

```
hugo new content topics/<desired file name>.md
```

The above command will create a new file in the `content/topics` directory. Fill in the front end matter (i.e. the variables at the top of the file and between two `---`) with appropriate value and start writing your content.

**Note:** To include the a dashboard or highlight under a specific topic, that topic should be mentioned in the front matter of the corresponding content.

### News

News are updates regarding the portal and maybe also the research and science on the node country. To add a news, run the following command from the repository's root. The `<desired file name>` in the command is the new file you want (but without spaces).

```
hugo new content news/<desired file name>.md
```

The above command will create a new file in the `content/news` directory. Fill in the front end matter (i.e. the variables at the top of the file and between two `---`) with appropriate value and start writing your content.

### Events

Events pages consists a list of upcomings events and trainings. To add a new event, copy the following fields (including the `{}` brackets) and paste at the top (after the opening bracket `[`) of the `data/events.json` file. Then fill in the neccessary information for the event.

```json
{
    "title": "",
    "type": "",
    "date_start": "",
    "time_start": "",
    "date_end": "",
    "time_end": "",
    "venue": "",
    "organisers": "",
    "event_url": "",
    "description": ""
},
```

**Tip:** As the time progresses, the data file might get bigger. So it might be better to cleanup (i.e. remove expired events) the file.

### New content

You can add a completely new content by creating a file (for single pages like about, contact, etc) or folder (for a section like dashboards, news, etc).

#### Single page

You can create a single page by directly creating a file under `content` directory. For example, creating `content/services.md` will create a new page and can be accesed via the URL `https://yourwebsite.com/services/`

If you desired to add the new page to menu i.e. the navigation bar at the top of the website, you have two options

1) To add in the top menu (i.e. same level as About, Contact, etc), add `navbar_top` to the `menu` in the front matter of the file as follows

    ```yaml
    ---
    title: Anytitle
    menu:
        navbar_top:
            name: <name>
            identifier: <identifier>
    ---
    ```

    Replace `<name>` and `<identifier>` with desired values. This will create an entry in the top navigation bar.

2) To add in the main menu (i.e. same level as Dashboards, Topics, etc), add `navbar_main` to the `menu` in the front matter of the file as follows

    ```yaml
    ---
    title: Anytitle
    menu:
        navbar_main:
            name: <name>
            identifier: <identifier>
    ---
    ```

    Replace `<name>` and `<identifier>` with desired values. This will create an entry in the main navigation bar.

#### Section

You can create a section by creating a folder and index file. For example, to create `content/services/_index.md` will create section `services` and you can further create single pages under that section. For example, creating `content/services/sequencing.md` will create a single page `sequencing` within the section `services`. To add new section and its pages in main menu as drop down, we would do as following (explained with before mentioned example)

1) Add the section index to the main menu i.e. considering above mentioned `services` example, you should add the following to `content/services/_index.md` file

    ```yaml
    ---
    title: Anytitle
    menu:
        navbar_main:
            name: Services
            identifier: services
            params:
                type: dropdown
                include_parent: true
    ---
    ```

    **Note:** The `type: dropdown` in the params will make the it a drop down in the main menu and `include_parent: true` will also include `content/services/_index.md` as one of the entry in the dropdown. If it is not desired it can be removed.

2) Add the single pages of the above created section to its dropdown i.e. considering the same example as step 1, you should add the following to `content/services/sequencing.md`

    ```yaml
    ---
    title: Anytitle
    menu:
        services:
            name: Sequencing
            identifier: sequencing
    ---
    ```

    **Note:** `services` is used instead of `navbar_main` as the `menu` key. We should use the `identifier` we used for the section index file (see step 1) as the key.

## Themes

This repository uses [node pathogens portal theme](https://github.com/ScilifelabDataCentre/node-pathogens-portal-theme) and it defines the layout and design that the content are displayed in the website.

### Layout

If you desire to create a new layout or replace the exisitng layouts. Just create a `layouts` directory and start filling it with your own loyout. For example

- creating `layout/dashboards/list.html` will affect how the `content/dashboards/_index.md` file is displayed
- creating `layout/dashboards/single.html` will affect how the `content/dashboards/internal_dash.md` (and other pahes within dashboards) are displayed

`hugo` layouts are sophisticated and you can read more about it [here](https://gohugo.io/templates/)

### Update theme

The [node pathogens portal theme](https://github.com/ScilifelabDataCentre/node-pathogens-portal-theme) might be updated from time to time, in case if you like to pull the latest changes, follow the steps below. 

1) Open a terminal and go to themes folder in the `hugo` project

    ```
    cd <hugo project path>/themes/node-pathogens-portal-theme
    ```

2) Once in the `themes/node-pathogens-portal-theme` run

    ```
    git checkout main
    ```

3) Pull the latest changes

    ```
    git pull origin main
    ```

4) Go back to project root again

    ```
    cd ../..
    ```

5) Add this change so that the lastest commit of the theme is linked to the hugo repo

    ```
    git add themes/node-pathogens-portal-theme
    ```

6) Commit the change and push to remote as usual

    ```
    git commit -m "Updated the theme"
    git push origin <branch name>
    ```

    **Note:** Above step have two commands and `<branch name>` will be the branch you are working on.

## Analytics

It can be useful to collect metrics for a website (like number of visits across the site and for each pages). There are several tools (free and paid) that can be used for this. Few examples [Google Analytics](https://developers.google.com/analytics/devguides/collection/ga4), [Motomo](https://matomo.org/), [Mixpanel](https://mixpanel.com/), etc

## Hosting

Hosting means getting the content to the internet, this can be done in different ways. Contact your university/group IT team regarding this, as there can be organisational policies/regulations on this.

## Credits

This project is supported by the National Institute Of Allergy And Infectious Diseases of the National Institutes of Health under Award Number U24AI183840. The content is solely the responsibility of the authors and does not necessarily represent the official views of the National Institutes of Health.

This site developed by [Scilifelab Data Centre](https://www.scilifelab.se/data/) as part of [PDN project](https://pathogendatanetwork.org/) and is based on [central pathogens portal](https://www.pathogensportal.org/), [Swedish pathogen portal](https://www.pathogens.se/) and [Swiss pathogen portal](https://pathogensportal.ch/).

We thank [Swiss Institute of Bioinformatics](https://www.sib.swiss/), [EMBL-EBI](https://www.ebi.ac.uk/) and all collaborators.
