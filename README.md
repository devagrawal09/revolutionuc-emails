# revolutionuc-emails

[![MIT License](https://img.shields.io/github/license/revolutionuc/revolutionuc-email.svg?maxAge=2592000)](LICENSE)
![stability-wip](https://img.shields.io/badge/stability-work_in_progress-yellow.svg)
[![Travis branch](https://img.shields.io/travis/revolutionuc/revolutionuc-emails.svg)](https://travis-ci.org/revolutionuc/revolutionuc-emails)
[![Dependencies Status](https://david-dm.org/revolutionuc/revolutionuc-email/status.svg)](https://david-dm.org/revolutionuc/revolutionuc-email)
[![Dependencies Status](https://david-dm.org/revolutionuc/revolutionuc-email/dev-status.svg)](https://david-dm.org/revolutionuc/revolutionuc-email?type=dev)

> Transactional and marketing email templates and builder for RevolutionUC

## Usage

Install the module as a dependency with `npm install --save revolutionuc-emails`. Next, use the api to build emails:

### api

The api allows the creation of html and plain text based transactional emails (ex: Mailgun).

```javascript
const Email = require('revolutionuc-emails')

const email = new Email()
const template = 'welcome' // choose from templates in `./templates/`
const templateData = {
  subject: 'Email subject', // required
  shortDescription: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.' // required, this is shown next to the subject in most email clients
}
email.build('html', template, templateData)
  .then(console.log) // resultant html as a string
  .catch(console.error)
```

### Marketing emails (templated)

The email builder allows templates to be built ready with variable placeholders for marketing purposes (ex: MailChimp).

## Develop

Get started hacking on revolutionuc-emails by:

```bash
git clone https://github.com/revolutionuc/revolutionuc-email.git
cd revolutionuc-email
npm install
```

### Creating a new email template

[Nunjucks](https://github.com/mozilla/nunjucks) is the templating engine used for all templates.

Start by creating a new template in `templates/`. For example, a new template could be called `awesome.njk` which extends `master.njk`. An example template looks like:

```njk
{% extends 'master.njk' %}

{% block body %}
<h1>My awesome template!</h1>
{% endblock %}
```

## The terrible truth about html emails

> The sad truth about creating or coding HTML emails is that tables are the only things that are universally supported when it comes to email design. If you came from the world of building websites, this may seem like a stepping into Doc Brown's Delorean, charging up the Flux-capitor, and going back to the 1996. Suddenly your CSS is written with inline style tags, useful CSS properties don't work and you're burried in a sea of table tags. General rule of thumb: your email is not going to look identical in every client. And that’s OK.
>
> -- [Zurb docs](http://foundation.zurb.com/emails/docs/tips-tricks.html#need-to-know) 

This project uses Zurb's [Inky](https://github.com/zurb/inky) library which allows us to write html5-like (inky) syntax and compile to old school html table based formats, so writing our email templates in a table format is not necessary!

## Tests

Run tests with `npm test`. Check code coverage with `npm run coverage`.
