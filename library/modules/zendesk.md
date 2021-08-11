---
description: >-
  Seamlessly integrate Zendesk with your favorite APIs, databases, and
  programming languages, using WayScript.
---

# Zendesk

![Provide customer support with Zendesk](../../.gitbook/assets/zendesk.png)

## 🔗 Link Your Zendesk Support Account

When using Zendesk module for the first time, follow the prompt to enter your Zendesk account subdomain and authorize access. More information on finding your subdomain can be found [here](https://support.zendesk.com/hc/en-us/articles/221682747-Where-can-I-find-my-Zendesk-subdomain-).

{% hint style="info" %}
You must have a Zendesk support account to fully use this module. If you do not have a Zendesk support account, you can still send anonymous requests using this module.
{% endhint %}

## ⚙ Modes

* **Act as an End User:** Execute actions as a user that generates support requests from any of the available support channels. End users don't have access to any of the administrator and agent features of Zendesk Support.
* **Act as an Agent:** Execute actions as a member of the support staff who is assigned tickets and interacts with end users as needed to resolve support issues. The agent's role and privileges are defined by admins.

## ✏ List

Allowed for end users and agents.

* **As end user**: Retrieve the requests made to a particular Zendesk support account. Potential actions:
  * List Requests
  * Search Requests
  * Show Request by ID
  * List Comments
  * Show Comment by ID
* **As agent**: Retrieve the tickets assigned to your Zendesk support account. Potential actions:
  * List Tickets
  * Search Tickets
  * Show Ticket\(s\)

#### 📥 Inputs

* **Request Recipient's Subdomain** - the Zendesk subdomain of the support account that received the request\(s\)
* **Request ID -** id associated with the request to be retrieved
* **Comment ID -** id associated with the comment to be retrieved
* **Ticket ID\(s\) -** id\(s\) associated with the ticket\(s\) to be retrieved
* **Query Phrase -** the phrase you want to search for in the requests/tickets

💡 **Advanced**

* **Sort By \(optional\) -** specify the method used for sorting output
* **Sort Order \(optional\) -** specify the sorting order of the output
* **Status \(optional\) -** specify the status of the requests displayed
* **Perform this Action on Multiple Tickets \(optional\) -** show multiple tickets by id
  * Enter a comma-separated list of ids

## 🌟 Create

Allowed for end users and agents.

* **As end user**: Make requests to a particular Zendesk support account. Potential actions:
  * Create a Request
* **As agent**: Make tickets to your Zendesk support account. Potential actions:
  * Create Ticket

#### 📥 Inputs

* **Recipient's Subdomain** - the Zendesk subdomain of the support account that will receive the request
* **Subject \(optional\) -** the subject of the request/ticket
* **Body -** the message of the request/ticket
* **Priority \(optional\)** - the priority associated with the request/ticket

💡 **Advanced**

* **Anon** **\(optional\)** - Send request anonymously \(does not require sign-in\)

## ⚡Update

Allowed for end users and agents.

* **As end user**: Update requests made to a particular Zendesk support account. Potential actions:
  * Add a Comment
* **As agent**: Update tickets in your Zendesk support account. Potential actions:
  * Update Ticket
  * Merge Tickets into Target Ticket
  * Mark Ticket\(s\) as Spam
  * Restore Deleted Ticket\(s\)

#### 📥 Inputs

* **Recipient's Subdomain** - the Zendesk subdomain of the support account that will receive the request
* **Request ID -** id associated with the request to be updated
* **Body \(optional for updating tickets; required for adding a comment\) -** the message of the updated ticket or additional comment
* **Ticket ID\(s\) -** id\(s\) associated with the ticket\(s\) to be updated
* **Priority \(optional\)** - the priority of the updated ticket
* **Status \(optional\)** - the status of the updated ticket
* **Target Ticket ID** - the id of the ticket that the tickets specified by the Ticket ID\(s\) input will be merged into
  * Tickets specified by the Ticket ID\(s\) input will be closed

💡 **Advanced**

* **Source Comment \(optional\) -** private comment to add to the target ticket
* **Target Comment \(optional\) -** private comment to add to the source ticket
* **Perform this Action on Multiple Tickets \(optional\)** - update multiple tickets
  * Enter a comma-separated list of ids

## 👋 Delete

Allowed for agents.

* **As agent**: Delete tickets from your Zendesk support account. Potential actions:
  * Delete Ticket\(s\)

#### 📥 Inputs

* **Ticket ID\(s\) -** id\(s\) associated with the ticket\(s\) to be deleted

💡 **Advanced**

* **Perform this Action on Multiple Tickets \(optional\)** - delete multiple tickets
  * Enter a comma-separated list of ids

## 📤 Output

* **JSON Data -** Raw JSON received from the endpoint. Example:

```text
request = {
    url : Url
    id : Int
    status : String
    priority : String
    type : String
    subject : String
    description : String
    organization_id : Int
    via : Object
    custom_fields : Array
    requester_id : Int
    collaborator_ids : Array
    email_cc_ids : Array
    is_public : Bool
    due_at : String
    can_be_solved_by_me : Bool
    created_at : String
    updated_at : String
    recipient : String
    followup_source_id : Int
    assignee_id : Int
    ticket_form_id : Int
    fields : Array
}
```

{% hint style="info" %}
If an error occurs, the full error message will be displayed as the JSON Data output.
{% endhint %}

