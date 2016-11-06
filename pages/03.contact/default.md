---
title: 'Contact Us'
forms:
    contact-form:
        message_color: danger
        fields:
            -
                name: name
                label: name
                placeholder: name
                type: text
                validate: { required: true }
                classes: form-control
            -
                name: email
                label: email
                placeholder: email
                type: email
                validate: { required: true }
                classes: form-control
            -
                name: phone
                label: phone
                placeholder: phone
                type: text
                classes: form-control
            -
                name: message
                label: message
                placeholder: message
                type: textarea
                rows: 5
                validate: { required: true }
                classes: form-control
        buttons:
            -
                type: submit
                value: send
                classes: 'btn btn-default'
        process:
            -
                email: { from: '{{ config.plugins.email.from }}', to: ['{{ config.plugins.email.from }}'], subject: '[Contact] {{ form.value.name|e }}', body: '{% include ''forms/data.html.twig'' %}' }
            -
                save: { fileprefix: contact-, dateformat: Ymd-His-u, extension: txt, body: '{% include ''forms/data.txt.twig'' %}' }
            -
                display: thank-you
            -
                reset: true
---

We'd love to hear from you.

> Install and configure whatever contact form plugin works for you.

