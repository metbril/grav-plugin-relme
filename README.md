# Rel Me Plugin

The **Rel Me** Plugin is for [Grav CMS](http://github.com/getgrav/grav). Add `rel="me"` links to your website in 2 ways.

1. Add `<link>` to the HTML `<head>` section or create a list.
2. Add an `<ul>` list somewhere on a page.

## Installation

Installing the Rel Me plugin can be done in one of two ways. The GPM (Grav Package Manager) installation method enables you to quickly and easily install the plugin with a simple terminal command, while the manual method enables you to do so via a zip file.

### GPM Installation (Preferred)

The simplest way to install this plugin is via the [Grav Package Manager (GPM)](http://learn.getgrav.org/advanced/grav-gpm) through your system's terminal (also called the command line).  From the root of your Grav install type:

    bin/gpm install relme

This will install the Rel Me plugin into your `/user/plugins` directory within Grav. Its files can be found under `/your/site/grav/user/plugins/relme`.

### Manual Installation

To install this plugin, just download the zip version of this repository and unzip it under `/your/site/grav/user/plugins`. Then, rename the folder to `relme`. You can find these files on [GitHub](https://github.com/metbril/grav-plugin-relme) or via [GetGrav.org](http://getgrav.org/downloads/plugins#extras).

You should now have all the plugin files under

    /your/site/grav/user/plugins/relme
	
> NOTE: This plugin is a modular component for Grav which requires [Grav](http://github.com/getgrav/grav) and the [Error](https://github.com/getgrav/grav-plugin-error) and [Problems](https://github.com/getgrav/grav-plugin-problems) to operate.

### Admin Plugin

If you use the admin plugin, you can install directly through the admin plugin by browsing the `Plugins` tab and clicking on the `Add` button.

## Configuration

Before configuring this plugin, you should copy the `user/plugins/relme/relme.yaml` to `user/config/plugins/relme.yaml` and only edit that copy.

Here is the default configuration and an explanation of available options:

```yaml
enabled: true
path:
active: true
icons: true
```

option | explanation
--- | ---
enabled | Enable the plugin
path | Path/route to the parent page of the menu items
active | If enabled, insert `<link>` tags in the page
icons | If enabled, show FontAwesome icons in the list

Note that if you use the admin plugin, a file with your configuration, and named relme.yaml will be saved in the `user/config/plugins/` folder once the configuration is saved in the admin.

## Usage

### Pages

1. Add a parent page. The route to this page should be added to the plugin configuration. Disable routing of the page.

2. Create child pages for each menu item that you want to include.

Front matter | Description
------------ | -----------
`title` | Displayed as the list title
`icon` | A FontAwesome icon. Defaults to 'link'.
`link` | The link to your profile page

### Link

Add this code to your template in the `<head>` section.

```twig
{% if config.plugins.relme.enabled %}
    {% include 'partials/relme-link.html.twig' %}
{% endif %}
```

### List

Optionally you can add a social menu to a page. For example in your sidebar. Add this code to your template:

```twig
{% if config.plugins.relme.enabled %}
    {% include 'partials/relme-list.html.twig' %}
{% endif %}
```

The list items can have icons. 
## Credits

This plugin provides [rel=me](https://indieweb.org/rel-me) functionality for the [IndieWeb](https://indieweb.org/).

## To Do

- [ ] Automatically inject link in HTML header
- [ ] Per page override of link injection
