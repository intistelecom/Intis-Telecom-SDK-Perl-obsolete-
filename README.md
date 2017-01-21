# Intis-Telecom-SDK-Perl


## Description
The Intis telecom gateway lets you send SMS messages worldwide via its API. This program sends HTTP(s) requests and receives information as a response in JSON and/or XML. The main functions of our API include:

* sending SMS messages (including scheduling options);
* receiving status reports about messages that have been sent previously;
* requesting lists of authorised sender names;
* requesting lists of incoming SMS messages;
* requesting current balance status;
* requesting lists of databases;
* requesting lists of numbers within particular contact list;
* searching for a particular number in a stop list;
* adding new templates;
* requesting monthly statistics;
* making HLR request;
* HLR request
* receiving HLR request statistics;
* requesting an operator’s name by phone number;

To begin using our API please [apply](https://go.intistele.com/external/client/register/) for your account at our website where you can get your login and API key.

## Pre-Install Perl Modules

* cpanm YAML::Tiny
* cpanm WWW::Mechanize
* cpanm Digest::Perl::MD5
* cpanm JSON
* cpanm Switch

## Install

* cpanm API::Intis

## Usage

### Configiration

1. Edit  config file config.yaml
    * login : you login
    * APIKey : you API key
2.  Set additional options in the hash.
```perl
my %addition_params = (state=> '6546546654');
```


## API
1. use API::Intis
2. Call API with method
```perl
my $ballance = API::Intis::APIRequest->new('balance');
```
where ('balance') - method. [Look list of methods](#aviable-methods). 
> $ballance - for example object name.

3. Call API with method with additional options
```perl
my $ballance = API::Intis::APIRequest->new('balance', \%addition_params);
```
*Note: list if  additional options. [Look list of methods](#aviable-methods).*

The names of the method are the name .php file

The response object contains the following attributes:

* Request is in the form of JSON
```perl
$ballance->{request_json};
```
* Request is in the form of XML
```perl
$ballance->{request_xml};
```
* Requested text description of the error
```perl
$ballance->{error};
```
* Requested hash
```perl
$ballance->{request_object};
```
* Requested outgoing format
```perl
$ballance->{out_format};
```
* Requested method
```perl
$ballance->{method};
```

## Aviable methods

| Method   |      Description      | Has Base / Additional params |
|----------|:-------------:|-------------:|
| balance |   Balance request | Base |
| base |     Lists request   | Base |
| senders |  Request for senders list | Base |
| phone |   Request for numbers from list | Base + Additional (base, page)|
| status |   Status request  | Base + Additional (state)|
| send |    SMS sending  | Base + Additional (phone, text, sender, sendingTime)|
| find_on_stop |   Search in the blacklist  | Base + Additional (phone)|
| add2stop |   Adding a number to the blacklist  | Base + Additional (phone)|
| add_template |  Adding a template  | Base + Additional (name, text, override) |
| del_template |  Deleting a template  | Base + Additional (name) |
| stat_by_month |  General statistics for a month  | Base + Additional (month) |
| hlr |   HLR request   | Base + Additional (phone) |
| hlr_stat |   Statistics of HLR requests  | Base + Additional (from, to) |
| operator |   Mobile operator query  | Base + Additional (phone, text) |
| incoming |   Request for incoming SMS  | Base + Additional (date, from, to) |
| prices |   Request for prices  | Base  |

> Base params - login, signature, timestamp. Param login and signature - is is obtained from the configuration file. [Look of configuration](#configiration), timestamp - is obtained automatically.


## License
The Perl script is released under the
[GPL license](https://opensource.org/licenses/GPL-2.0).