---
title: "Contáctenos"
layout: contact
lang: es
permalink: /es/contact/
description: "¿Tiene un proyecto en mente o desea conocer más sobre nuestros servicios de visión por computadora? Nos encantaría escucharle."
---

{% assign t = site.data.translations[page.lang] %}

{{ t.contact_page.intro }}

<form action="{{ site.contact_form_action }}" method="POST" class="contact-form mt-2">
  <div class="mb-2">
    <label for="name"><strong>{{ t.contact_page.name_label }}</strong></label><br/>
    <input type="text" id="name" name="name" required style="width:100%;padding:0.5rem;border:1px solid #ccc;border-radius:4px;margin-top:0.25rem;" />
  </div>
  <div class="mb-2">
    <label for="email"><strong>{{ t.contact_page.email_label }}</strong></label><br/>
    <input type="email" id="email" name="_replyto" required style="width:100%;padding:0.5rem;border:1px solid #ccc;border-radius:4px;margin-top:0.25rem;" />
  </div>
  <div class="mb-2">
    <label for="message"><strong>{{ t.contact_page.message_label }}</strong></label><br/>
    <textarea id="message" name="message" rows="5" required style="width:100%;padding:0.5rem;border:1px solid #ccc;border-radius:4px;margin-top:0.25rem;"></textarea>
  </div>
  <input type="hidden" name="_subject" value="{{ t.contact_page.subject }}" />
  <button type="submit" class="button button-primary">{{ t.contact_page.submit_label }}</button>
</form>
