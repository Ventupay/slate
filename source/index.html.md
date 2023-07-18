---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - python
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: EFEX API
    content: Documentation for the EFEX API
---

# Introduction to EFEX

EFEX is a fintech that helps companies automate and process nearly instant cross-border payments with $0 transaction fees, competitive exchange rates, and automated local dispersion.


# EFEX's API

The purpose of this documentation is to guide you through the implementation of our API that allows any company to automate their FX operations and international payments.

Our API currently accepts deposits in: 

- United States (USD)
- Mexico (MXN) 
- Colombia (COP)

In addition, our API allows our users to make instant payouts in:

- United States (USD)
- Mexico (MXN)
- Colombia (COP)
- **Rest of the world (SWIFT in USD)

# Know Your Business (KYB)

To start operating with EFEX your company needs to complete the Know Your Bussiness (KYB) registration process in the following link: https://app.efexpay.com/register 

Our compliance team will review your documentation and answer in under 24 hours.


<aside class="notice">
Uploading your company's documentation should not take more than 5 minutes. 
</aside>

# Glossary

- Company: refers to the customer that is integrating to EFEX's API in order to automate its foreign exchange operations and international dispersions
- "My team": owners, admins, and other members of the company with access to the EFEX platform and APIs
- Contacts: third party recipients and beneficiaries of transfers made by a Company
- Payments Out: this includes both the conversions between different currencies + the dispersion to the final contacts
- Operations: refers to all the endpoints that execute an action in the flow of funds with EFEX's API

# Environments

We currently have 2 environments: a sandbox environment in which testing can be carried out and a production environment where you can start executing your operations.

## Access to Sandbox Environment

Once your KYB onboarding process has been approaved, please send an email to santiago@efexpay.com requesting the Sandbox keys. 

```python
Example key: key= cdf5f162-e7cd-4e3d-b781-37dfcd4100b

URL_SANDBOX: https://sandbox.efexpay.com/
```

## Access to Production Environment
Once you have finalized the integration in the Sandbox environemnt, EFEX will give you your official API keys to start executing operations.

```python
Example key: key= 0bpqwkas2818-129412SAJ0102mdks1002

URL_PROD: https://app.efexpay.com/
```


# Platform vs API Functionalities

At EFEX, we want to give you the best product experience. Hence, we offer both a platform where you and your entire team can excecute transactions manually, and a comprehensvie API (connected to your platform) where you can automate with code all your operations. 

Our platform includes the following features:

- Instructions to add funds to your EFEX wallet
- Withdrawal of funds from your EFEX wallet
- Visibility of exchange rates between currencies
- Creation of contacts
- Payments out (Send payments)
- Payments in (Request payments) **Currently to other EFEX users
- Payment receipts
- Monthly statements
- Add and remove members to your EFEX account


Our API includes the following functionalities:

- Instructions to add funds to your EFEX wallet
- Visibility of exchange rates between currencies
- Creation of contacts
- Payments out (Send payments)


# Instructions to Add Funds

In order to carry out an operation, we first need to load funds into your EFEX wallet. This must be done from your company's bank account to your EFEX wallet in the corresponding country.

<aside class="notice">
Warning: it is important that the funds come from the bank account registered in the onboarding so that we can identify the funds internally in EFEX.
</aside>

Deposit methods that we accept:

- United States (USD): domestic wires (we don't accept ACH)
- Mexico (MXN): SPEI
- Colombia (COP): PSE

<aside class="notice">
Warning: if I register as a US company, I can only add funds within the US
</aside>


# Exchange rates

At any time, you can query via API the exchange rates between the different currencies that we support:

USD/MXN
<br>
USD/COP
<br>
MXN/USD
<br>
USD/COP
<br>
COP/USD
<br>
COP/MXN

It is important to keep in mind that the exchange rates are informative in order to know the market prices that EFEX currently offers. However, to carry out a currency conversion, it is necessary to execute the "Payments Out" API that includes the FX (the conversion) plus the local dispersion to the destination bank.

# Contact Creation

The creation of contacts is a process by which your company can generate end beneficiaries for transfers in the countries of destination. Contacts can be persons or businesses. For the creation of contacts we need the following data depending on the country.

Attribute | Type | Description | Example
--------- | ------- | ----------- | -----------
id | UUID | the id of the Contact | a9d0164d-22df-46c6-a836-1a3da5a470d8
email | Email | Email of the Contact | info@company.com
phone | String | Phone Number of the Contact | 6505056442
phone_country	 | String | 2 letter ISO code of the country the phone number exists in | US
tax_number | TaxNumber | tax number of the contact for the country provided | 128412312
first_name | String | First name of the Contact | Santiago
last_name | String | Last name of the Contact | Bustamante Villa
address | String | address of Contact | 350 Sharon Park Dr
city | String | city of the Contact	| Menlo Park
state | String | state of the Contact | California
postal_code	 | String | the postal code of the beneficiary | 94025
country | String | 2 letter ISO code of the country the Contact resides in | US
business_name | String | Name of recipient business if applicable | Trator LLC
account_number | String | the IBAN, CLABE, or account number of the bank account | 2345366431
routing_code | String | Only applicable for US contacts | 021000021
currency | String | the 3 character code of the currency | USD
bank_name | String | the name of the banking institution | JP Morgan


# Payments Out

With the endpoint of "Payments Out" you can make all conversions and dispersions internationally. In order to send a payment we need to identify with the email a beneficiary previously created with the "Contacts" endpoint. With the "client_uuid" of that contact you will be able to call this "payload" to carry out the transaction and automatically send the funds.



# This is under development

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete


# Add Team Members

You can access your EFEX account in the following link to invite other members of your company: https://app.efexpay.com/login
<br>
You can give them reading or admin permissions to your EFEX platform.

# Contact us

Please always feel free to contact us either for technical support or to create your EFEX account!

- Sales: sales@efexpay.com
- Technical support: info@efexpay.com