---
title: "Contact Us"
layout: contact
description: "Have a project in mind or want to learn more about our computer vision services? We'd love to hear from you."
---

Whether you have a specific project in mind or just want to explore what's possible with computer vision, reach out — we're happy to talk.

<form action="{{ site.contact_form_action }}" method="POST" class="contact-form mt-2">
  <div class="mb-2">
    <label for="name"><strong>Name</strong></label><br/>
    <input type="text" id="name" name="name" required style="width:100%;padding:0.5rem;border:1px solid #ccc;border-radius:4px;margin-top:0.25rem;" />
  </div>
  <div class="mb-2">
    <label for="email"><strong>Email</strong></label><br/>
    <input type="email" id="email" name="_replyto" required style="width:100%;padding:0.5rem;border:1px solid #ccc;border-radius:4px;margin-top:0.25rem;" />
  </div>
  <div class="mb-2">
    <label for="message"><strong>Message</strong></label><br/>
    <textarea id="message" name="message" rows="5" required style="width:100%;padding:0.5rem;border:1px solid #ccc;border-radius:4px;margin-top:0.25rem;"></textarea>
  </div>
  <input type="hidden" name="_subject" value="New enquiry from VisionTech Solutions website" />
  <button type="submit" class="button button-primary">Send Message</button>
</form>
