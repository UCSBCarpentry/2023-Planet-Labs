---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "UC Santa Barbara Library"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Room 2509, Davidson Library, 525 U-Cen Rd, Santa Barbara, CA"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "us"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: 34.413958        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: -119.845491       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "May 12, 2023"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 am - 4:30 pm PST"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2023-05-12      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2023-05-12        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Kristi Liu", "Jon Jablonski","Octave Lepinard"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Helper"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["dreamlab@library.ucsb.edu"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:   600864159877  # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

<h2>Registration for this workshop begins on April 7, 2023 at 8:00 am PST.</h2>

{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="400px"
  scrolling="auto">
</iframe>
<strong>Some adblockers block the registration window. If you do not see the
  registration box above, please check your adblocker settings.</strong>
{% endif %}


<h2 id="general">General Information</h2>


{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<p>
This is a one-day workshop to learn about UCSB's new three-year licenses for accessing Planet Labs imagery, web applications, and visualization tools. Planet provides daily satellite imagery of the Earth’s land surfaces and coastal areas. UCSB’s access includes the RapidEye Archive, SkySat Archive, and daily PlanetScope imagery.  In the morning we will introduce Planet and the available products, some use cases, and past research, finishing with how to access the imagery using our web platform. The afternoon workshop will start with how to access imagery and go over the basics of using the ArcGIS interface (Planet Labs Plug-in) followed by an introduction to Planet's APIs and how to leverage them for bulk download/automating your workflow. This session will end with an open discussion/Q&A with Planet Labs representatives on how to use Planet data for any future research or projects. 
</p>
<hr/>