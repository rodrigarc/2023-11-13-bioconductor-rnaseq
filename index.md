---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "Instituto Evandro Chagas, Belém, Brasil;"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Av. Almirante Barroso, 492, Belém, Pará"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "br"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "pt"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "-1.45"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-48.50"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Novembro 13-15, 2023"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 - 16:00 GMT-3"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2023-11-13      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2023-11-15        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Rodrigo Arcoverde Cerveira da Silva"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Edivaldo Costa Souza Júnior"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["rodrigo.arcoverde@ki.se","rodrigo.arcoverdi@gmail.com", "edivaldo.junior@iec.gov.br"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
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
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-geospatial" or site.curriculum == "dc-image" or site.curriculum == "dc-socsci" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-image</code>, <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}



<h2 id="general">Informações gerais</h2>

{% comment %}
INTRODUÇÃO

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% if site.pilot %}
A Bioconductor Carpentries desenvolve e ministra workshops sobre as habilidades fundamentais de dados necessárias para conduzir análises de dados ômicos. Seu público-alvo são pesquisadores experimentais que têm pouca ou nenhuma experiência computacional anterior, e suas lições são específicas de um domínio, com base no conhecimento existente dos alunos para capacitá-los a aplicar rapidamente as habilidades aprendidas em suas próprias pesquisas. Os participantes serão incentivados a ajudar uns aos outros e a aplicar o que aprenderam aos seus próprios problemas de pesquisa.

Este é um workshop piloto, testando uma lição que ainda está em desenvolvimento. Os autores da lição apreciariam qualquer feedback que você pudesse dar sobre o conteúdo da lição e sugestões sobre como ela poderia ser melhorada.
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://www.latlong.net/ to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="onde">
  <strong>Onde:</strong>
  {{page.address}}.
</p>
{% elsif online == "true_public" %}
<p id="onde">
  <strong>Onde:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="onde">
  <strong>Onde:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="quando">
  <strong>Quando:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requisitos">
  <strong>Requisitos:</strong>
  {% if online == "false" %}
Os participantes terão acesso a computadores com laptop com
     Sistema operacional Mac, Linux ou Windows com R ( > v 4.0.0) e RStudio instalados. 
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
</p>

{% comment %}
Acessibilidade

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="acessibilidade">
  <strong>Acessibilidade:</strong>
{% if online == "false" %}
 Estamos empenhados em tornar este workshop
   acessível a todos. Para workshops em locais físicos, os organizadores dos workshops verificaram se:
</p>
<ul>
  <li>O local é acessível para cadeiras de rodas/scooter.</li>
  <li>Banheiros acessíveis estão disponíveis.</li>
</ul>
<p>
   Os materiais serão fornecidos antes do workshop e
   folhetos em letras grandes estão disponíveis, se necessário, notificando o
   organizadores com antecedência. Se pudermos ajudar a tornar o aprendizado mais fácil para
   você (por exemplo, intérpretes de linguagem de sinais, instalações de lactação), por favor
   entre em contato (usando os dados de contato abaixo) e nós
   tentar fornecê-los.
</p>
{% else %}
  Estamos empenhados em fornecer um ambiente de aprendizagem positivo e acessível para todos. Por favor
   notificar os instrutores com antecedência do workshop se você precisar de alguma acomodação ou se houver
   tudo o que pudermos fazer para tornar este workshop mais acessível para você.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contato">
  <strong>Contato:</strong>
  Por favor contate
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
  para mais informações.
</p>

<p id="função">
  <strong>Função:</strong>
  Para saber mais sobre as funções no workshop (quem fará o quê),
  referira-se <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop"> ao nosso FAQ do workshop </a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
Código de conduta
{% endcomment %}
<h2 id="code-of-conduct">Código de conduta</h2>

<p>
Todos os que participam nas atividades da Carpintaria são obrigados a cumprir o <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Código de Conduta</a>. Este documento também descreve como relatar um incidente, se necessário.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Relatar um Incidente de Código de Conduta</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
Questionários - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Questionários</h2>
<p>Certifique-se de preencher essas pesquisas antes e depois do workshop.</p>
{% if site.carpentry == "incubator" %}
<p><a href="{{ site.incubator_pre_survey }}">Pré-workshop Survey</a></p>
<p><a href="{{ site.incubator_post_survey }}">Pós-workshop Survey</a></p>
{% elsif site.incubator_pre_survey or site.incubator_post_survey %}
<div class="alert alert-danger">
WARNING: you have defined custom pre- and/or post-survey links for
a workshop not configured for The Carpentries Incubator
(the value of `curriculum` is not set to `incubator` in `_config.yml`).
Please comment out the `incubator_pre_survey` and `incubator_post_survey` fields
in `_config.yml` or, if this workshop is teaching a lesson in the Incubator,
change the value of `carpentry` to `incubator`.
</div>
{% else %}
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Questionário pré-workshop</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Questionário pós-workshop</a></p>
{% endif %}

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="cronograma">Cronograma</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% elsif site.carpentry == "bioc" %}		
{% include bioc/schedule.html %}
{% elsif site.carpentry == "incubator" %}
{% include custom-schedule.html %}
This workshop is teaching a lesson in [The Carpentries Incubator](https://carpentries-incubator.org/).

{% endif %}

{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom-schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}

{% if site.pilot %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. Please [contact the workshop organisers](#contact) if you would like more information about the planned schedule.
{% endif %}

<hr/>


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  Para participar nesse
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  você vai precisar de acesso aos Sofwares descritos abaixo.
  Além disso, você precisará de um navegador atualizado.
</p>
<p>
  Mantemos uma lista de problemas comuns que ocorrem durante a instalação como referência para os instrutores, o que pode ser útil na
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">página do wiki Problemas e Soluções de 
  Configuração</a>.
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instructions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "incubator" %}
Por favor, confira a página "Summary and Setup" do
[site da lição]({{ site.incubator_lesson_site }}) para obter instruções sobre como obter o software e os dados necessários para seguir a lição.
{% endif %}
