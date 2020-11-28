```jinja2
			<!--
{% macro addCell(index) %}
    {% if index<=49 %}
    <div class="docrank">
        {% if sortway != 2 %}
        {% if rank != None %}
            排名:{{ rank }}
        {% else %}
            排名:{{ index+1 }}
        {% endif %}
        {% endif %}
    </div>
        <ul class="docul" align="center">
            <li class="docli"><p>寝室号:</p>{{ infoes[index][0] }}
            <li class="scoreli"><p><b>荣誉次数:</b></p><p class="scorep">{{ infoes[index][1] }}</p></li>
        </ul>
    </div>
    {% endif %}
{% endmacro %}

{# a macro to add colume #}
{% macro addColumn(domindex,i) %}
    {% set index = domindex*3+i %}
        {% if index <= 49 %}
    <td>
    {% if index <3 and isTextSearch==False %}
    <a id="domhref" href="{{ url_for('displayDom',dominame = infoes[index][0] ) }}">
    {% endif %}

    {% if index == 0 and sortway==1 and isTextSearch==False %}
    <div class="docbox" style="background-color:#FFB90F">
        {% elif index == 1 and sortway==1 and isTextSearch==False %}
    <div class="docbox" style="background-color:Silver">
        {% elif index == 2 and sortway==1 and isTextSearch==False %}
    <div class="docbox" style="background-color:#4876FF">
        {% else %}
    <div class="docbox">
    {% endif %}
    {{ addCell(index) }}</div>
        {% if index <3 and isTextSearch==False %}
    </a>
    {% endif %}
    </td>
    {% endif %}
{% endmacro %}

{# add context in html #}
<table class="domtable">
{% if isTextSearch==False %}
{% set remainIndex=(infoes|count)%3 +1 %}
{% for domindex in range(infoes|count//3) %}
    <tr align="center">

            {{ addColumn(domindex,0) }}
            {{ addColumn(domindex,1) }}
            {{ addColumn(domindex,2) }}
    </tr>
{% endfor %}
{% else %}
    <tr align="center">
            {{ addColumn(0,0) }}
    </tr>
{% endif %}
</table>			
-->
```