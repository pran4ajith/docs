---
layout: page
weight: 0
title: Customer Subuser Invalid Emails
navigation:
   show: true
---

{% anchor h2 %}
Retrieve Invalid Emails 
{% endanchor %}


{% parameters get %}
 {% parameter 'user' 'Yes' 'Customer subuser must be registered under your account' 'The customer subuser we are retrieving invalid emails from' %}
 {% parameter 'task' 'Yes' 'Must be set to <em>get</em>' 'This will allow you to retrieve the invalid emails for the specified customer subuser' %}
 {% parameter 'date' 'No' 'Must be set to 1' 'Retrieves the timestamps, it will return a date in a MySQL timestamp format - YYYY-MM-DD HH:MM:SS' %}
 {% parameter 'method' 'Yes' 'Must be set to <em>invalidemails</em>' 'Allows you to access invalid email functionality' %}
{% endparameters %}


{% apiexample get POST https://api.sendgrid.com/apiv2/reseller.subuserManage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=invalidemails&user=example@example.com&task=get&date=1 %}
  {% response json %}
[
  {
    "email": "isaac@hotmail.comm",
    "reason": "Mail domain mentioned in email address is unknown",
    "created": "2009-06-01 19:41:39"
  },
  {
    "email": "isaac@hotmail",
    "reason": "Bad Syntax",
    "created": "2009-06-01 19:41:39"
  },
  {
    "email": "isaac@example.com",
    "reason": "Known bad domain",
    "created": "2009-06-01 19:41:39"
  }
]
  {% endresponse %}
  {% response xml %}
<invalidemails>
   <invalidemail>
      <email>isaac@hotmail.comm</email>
      <reason>Mail domain mentioned in email address is unknown</reason>
      <created>2009-06-10 12:40:30</created>
   </invalidemail>
   <invalidemail>
      <email>isaac@hotmail</email>
      <reason>Bad Syntax</reason>
      <created>2009-06-10 12:40:30</created>
   </invalidemail>
   <invalidemail>
      <email>isaac@example.com</email>
      <reason>Known bad domain</reason>
      <created>2009-06-10 12:40:30</created>
   </invalidemail>
</invalidemails>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Delete Invalid Emails 
{% endanchor %}

Since SendGrid does not deliver to invalid emails, users can remove invalid emails from their list at any time if re-delivery to a spam reported address is desired.


{% parameters delete %}
 {% parameter 'user' 'Yes' 'Customer subuser must be registered under your account' 'The customer subuser we are retrieving invalid emails from' %}
 {% parameter 'task' 'Yes' 'Must be set to <em>delete</em>' 'This will allow you to delete an invalid email for the specified customer subuser' %}
 {% parameter 'email' 'No' 'Must be an invalid email' 'You must specify the invalid emails to remove' %}
 {% parameter 'method' 'Yes' 'Must be set to <em>invalidemails</em>' 'Allows you to access invalid email functionality' %}
{% endparameters %}


{% apiexample delete POST https://api.sendgrid.com/apiv2/reseller.subuserManage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=invalidemails&user=example@example.com&task=delete&email=invalidemail@example.com %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}
