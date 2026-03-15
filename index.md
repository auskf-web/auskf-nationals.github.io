---
layout: landing-page
---

**Dates**  
**{{ site.tournament_date_with_day }}** - Tournament

**Tournament Venue**  
{% if site.venue_determined == true -%}
{{ site.venue_address_1 }}  
{{ site.venue_address_2 }}  
{{ site.venue_address_3 }}  
{{ site.venue_address_4 }}
{% else %}
Venue TBD  
{{ site.tournament_location_city_state }}
{% endif %}

Please email [competition@auskf.org](mailto:competition@auskf.org?Subject=AUSKF%20Nationals%20{{ site.tournament_year }}) for more information.

[Banner photo]({{ site.banner_url }}) of {{ site.banner_description }} courtesy of {{ site.banner_photographer }}.
