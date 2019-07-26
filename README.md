# ApiExtend MantisBT Plugin

[![app-type](https://img.shields.io/badge/category-mantisbt%20plugins-blue.svg)](https://github.com/spmeesseman)
[![app-lang](https://img.shields.io/badge/language-php-blue.svg)](https://github.com/spmeesseman)
[![app-publisher](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-app--publisher-e10000.svg)](https://github.com/spmeesseman/app-publisher)

[![authors](https://img.shields.io/badge/authors-scott%20meesseman-6F02B5.svg?logo=visual%20studio%20code)](https://github.com/spmeesseman)
[![GitHub issues open](https://img.shields.io/github/issues-raw/spmeesseman/ApiExtend.svg?maxAge=2592000&logo=github)](https://github.com/spmeesseman/ApiExtend/issues)
[![GitHub issues closed](https://img.shields.io/github/issues-closed-raw/spmeesseman/ApiExtend.svg?maxAge=2592000&logo=github)](https://github.com/spmeesseman/ApiExtend/issues)

- [ApiExtend MantisBT Plugin](#ApiExtend-MantisBT-Plugin)
  - [Description](#Description)
  - [Installation](#Installation)
  - [REST API](#REST-API)
    - [GET: /plugins/ApiExtend/api/issues/count/{project}/{type}](#GET-pluginsApiExtendapiissuescountprojecttype)
    - [GET: /plugins/ApiExtend/api/issues/countbadge/{project}/{type}](#GET-pluginsApiExtendapiissuescountbadgeprojecttype)

## Description

This plugin extends the MantisBT REST API.  This plugin was developed and tested on MantisBT 2.21.1.

## Installation

Extract the release archive to the MantisBT installations plugins folder:

    cd /var/www/mantisbt/plugins
    wget -O ApiExtend.zip https://github.com/spmeesseman/Releases/releases/download/v1.0.0/ApiExtend.zip
    unzip ApiExtend.zip
    rm -f ApiExtend.zip

Ensure to use the latest released version number in the download url.

Install the plugin using the default installation procedure for a MantisBT plugin in `Manage -> Plugins`.

For Apache configuration, see the example Location directive found in api/apache2-site-config

## REST API

The extended REST API can be authenticated in one of two ways:

1. Set the API user and API token in the Plugin settings for dedicated API acess using one static account.
2. Set the `Authorization` header value to a user API token for specific user access.

In either case, the token can be created in User Preferences for the user that will be used to make the requests under.

In case 1, the authroization token can be sent as a GET or POST parameter as opposed to having to be sent in the header.  This allows the svg badges to be linked to from within a README file.

For example:

    Authorization: DvhKlx9_g5dNkBEI4jqVmwAxaN9a1y3P

The following endpoints are available to automatically create/update releases with assets/files:

### GET: /plugins/ApiExtend/api/issues/count/{project}/{type}

Retrieves an issues count for open or closed issues.

Where `project` is the MantisBT project name

Where `type` is one of 'open' or 'closed'.

Example JSON Response Body

    {
        "count": 132
    }

### GET: /plugins/ApiExtend/api/issues/countbadge/{project}/{type}

Retrieves an issues count badge for open or closed issues, for use in readme files.

![badge1](res/badges.png)

Where `project` is the MantisBT project name

Where `type` is one of 'open' or 'closed'.
