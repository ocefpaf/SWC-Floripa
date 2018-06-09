---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "swc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc")
venue: "UFSC"        # brief name of host site without address (e.g., "Euphoric State University")
address: "Campus Reitor João David Ferreira Lima, s/n - Trindade, Florianópolis - SC, 88040-900"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: "br"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1)
language: "pt"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/ISO_639-1)
latlng: "-27.5982559,-48.5203502"       # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use http://www.latlong.net/)
humandate: "Jun 11,12,13 e 18-19, 2018"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "18:30-20:30"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2018-06-11      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2018-06-19        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Filipe Fernandes"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Vini Salazar, Juliana Leonel"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["ocefpaf@gmail.com"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:             # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
  HEADER

  Edit the values in the block above to be appropriate for your workshop.
  If the value is not 'true', 'false', 'null', or a number, please use
  double quotation marks around the value, unless specified otherwise.
  And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

{% comment %}
  EVENTBRITE

  This block includes the Eventbrite registration widget if
  'eventbrite' has been set in the header.  You can delete it if you
  are not using Eventbrite, or leave it in, since it will not be
  displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="248px"
  scrolling="auto">
</iframe>
{% endif %}

<h2 id="general">Informações Gerais</h2>

{% comment %}
  INTRODUCTION

  Edit the general explanatory paragraph below if you want to change
  the pitch.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  AUDIENCE

  Explain who your audience is.  (In particular, tell readers if the
  workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  LOCATION

  This block displays the address and links to maps showing directions
  if the latitude and longitude of the workshop have been set.  You
  can use http://itouchmap.com/latlong.html to find the lat/long of an
  address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Onde:</strong>
  {{page.address}}.
  Direções com
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
  DATE

  This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>Quando:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
  SPECIAL REQUIREMENTS

  Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requisitos:</strong> Participantes devem trazer um laptop com
  sistems operacionais Mac, Linux, ou Windows (tablets, Chromebooks, etc não poderão ser utilizados.) com privilégios de administradores.
  O laptop deve ter alguns pacotes de Software específicos instalados (lista
  <a href="#setup">abaixo</a>). Participantes também devem seguir o {% if page.carpentry == "swc" %}
  Software Carpentry's
  {% elsif page.carpentry == "dc" %}
  Data Carpentry's
  {% elsif page.carpentry == "lc" %}
  Library Carpentry's
  {% endif %}
  <a href="{{site.swc_site}}/conduct.html">Código de Conduta</a>.
</p>

<!-- {% comment %}
  ACCESSIBILITY

  Modify the block below if there are any barriers to accessibility or
  special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop
  accessible to everybody.
  The workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p> -->

{% comment %}
  CONTACT EMAIL ADDRESS

  Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contato</strong>:
  Para mais informações envie e-mail para
  {% if page.email %}
    {% for email in page.email %}
      {% if forloop.last and page.email.size > 1 %}
        or
      {% else %}
        {% unless forloop.first %}
        ,
        {% endunless %}
      {% endif %}
      <a href='mailto:{{email}}'>{{email}}</a>.
    {% endfor %}
  {% else %}
    to-be-announced
  {% endif %}
</p>

<hr/>

{% comment %}
  SCHEDULE

  Show the workshop's schedule.  Edit the items and times in the table
  to match your plans.  You may also want to change 'Day 1' and 'Day
  2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Cronograma</h2>

{% comment %} DO NOT EDIT SURVEY LINKS {% endcomment %}
<p><em>Questionários</em></p>
{% if page.carpentry == "swc" %} 
<p>Por favor complete esses questionários antes e depois do workshop.</p>
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pré-workshop </a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Pós-workshop </a></p>
{% elsif page.carpentry == "dc" %}
  <p>Por favor complete esses questionários antes e depois do workshop.</p>
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Pré-workshop </a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Pós-workshop </a></p>
{% elsif page.carpentry == "lc" %}
<p>Ask your instructor about pre- and post-workshop Survey details.</p>
{% endif %}


{% if page.carpentry == "swc" %}
  {% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/schedule.html %}
{% endif %}

{% comment %}
  Collaborative Notes

  If you want to use an Etherpad, go to

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  where 'YYYY-MM-DD-site' is the identifier for your workshop,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}

<hr/>

{% comment %}
  SYLLABUS

  Show what topics will be covered.

  1. If your workshop is R rather than Python, remove the comment
     around that section and put a comment around the Python section.
  2. Some workshops will delete SQL.
  3. Please make sure the list of topics is synchronized with what you
     intend to teach.
  4. You may need to move the div's with class="col-md-6" around inside
     the div's with class="row" to balance the multi-column layout.

  This is one of the places where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Ementa</h2>

{% if page.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}

<hr/>

<h2 id="setup">Instalação</h2>

<p>
  Para participar no workshop do
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %},
  você deve ter acesso aos Software abaixo.
  Adicionalmente, você necessitará de um browser atualizado.

  Para maiores informações por chequem a
  <a href="{{ page.root }}{% link setup.md %}">página de instalação de pacotes.</a>
</p>

<div id="editor"> {% comment %} Start of 'editor' section. {% endcomment %}
  <h3>Editor de Texto</h3>

  <p>
    Recomendados o <a href="https://code.visualstudio.com/#alt-downloads">VS code</a>
    para para edição de texto/código durante to workshop.
    Entretanto qualquer editor de texto que o participante se sentir confortável
    é adequado para o curso.
  </p>
