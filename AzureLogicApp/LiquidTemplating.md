#Documentation : https://shopify.github.io/liquid/basics/introduction/
##Sample Template
{
    "items": [
        {%- for employee in content.items -%}
        {
            "PersonNumber" : "{{ employee.PersonNumber }}",
            "DateOfBirth" : "{{ employee.DateOfBirth }}",
            {% if employee.names.size > 0 %}
            {% for name in employee.names %}
            "Salutation" : "{{ name.Title }}",
            "DisplayName" : "{{ name.DisplayName }}",
            "EffectiveStartDate" : "{{ name.EffectiveStartDate }}",
            {% endfor %}
            {% else %}
            "Salutation" : "",
            "DisplayName" : "",
            "EffectiveStartDate" : "",
            {% endif %}
            {% if employee.emails.size > 0 %}
            {% for email in employee.emails %}
            "WorkEmail" : "{{ email.EmailAddress }}",
            "UserName" : "{{ email.EmailAddress }}",
            {% endfor %}
            {% else %}
            "WorkEmail" : "",
            "UserName" : "",
            {% endif %}
            {% if employee.addresses.size > 0 %}
            {% for addresse in employee.addresses %}
                "Region2" : "{{ addresse.Region2 }}",
            {% endfor %}
            {% else %}
                "Region2": "",
            {% endif %}
            {% if employee.legislativeInfo.size > 0 %}
            {% for legislative in employee.legislativeInfo %}
                "Gender" : "{{ legislative.Gender }}",
            {% endfor %}
            {% else %}
                "Gender": "",
            {% endif %}
            {% if employee.workRelationships.size > 0 %}
            {% for workRelationship in employee.workRelationships %}
                "LegalEntityId" : {{ workRelationship.LegalEntityId }},
                "LegislationCode" : "{{ workRelationship.LegislationCode }}",
                "TerminationDate":
                {%- if workRelationship.TerminationDate != '' -%}"{{ workRelationship.TerminationDate }}",{%- else -%}null,{%- endif -%}
            {% endfor %}
            {% else %}
                "LegalEntityId": 0,
                "LegislationCode": "",
                "TerminationDate": null,
            {% endif %}
        },
        {%- endfor -%}
    ]
}

##Usage 
https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-enterprise-integration-liquid-transform?tabs=consumption