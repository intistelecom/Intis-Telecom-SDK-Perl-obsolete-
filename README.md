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
* requesting lists of templates;
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
my $ballance = APIRequest->new('balance');
```

The names of the method are the name .php file

The response object contains the following attributes:

* The answer is in the form of JSON
```perl
$ballance->{request_json};
```
* The answer is in the form of XML
```perl
$ballance->{request_xml};
```
* Text description of the error
```perl
$ballance->{error};
```
* Request hash
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

## License
The JavaScript MD5 script is released under the
[MIT license](http://www.opensource.org/licenses/MIT).