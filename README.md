<img style="border-radius: 8px" width="100%" src="https://i.ibb.co.com/R6CFG73/yaml-github-banner.png" alt="learning-yaml-banner-image"/>

# YAML - Introduction

YAML is one of the most popular data [`serialization languages`](https://devopedia.org/data-serialization), and it is used mostly for writing configuration files. The YAML recursive acronym stands for **YAML Ain’t Markup Language**. This language is designed with flexibility and accessibility in mind, so it’s human-readable and simple to understand. YAML works with all modern programming languages and is widely used in data persistence, internet messaging, cross-language data sharing, and many other places. YAML files either have the extension .yaml or .yml.

All of these factors contribute to YAML’s popularity as a configuration language in the DevOps domain, where it is widely used with well-known tools such as Kubernetes, Ansible, and Terraform.

- [YAML - Introduction](#yaml---introduction)
  - [What is a YAML used for?](#what-is-a-yaml-used-for)
- [Basic YAML Syntax](#basic-yaml-syntax)
- [YAML Data types](#yaml-data-types)
  - [Scalar data type:](#scalar-data-type)
    - [Numeric Data type](#numeric-data-type)
    - [String](#string)
  - [Lists:](#lists)
  - [Dictionaries](#dictionaries)
- [YAML Styles](#yaml-styles)
  - [Block Style](#block-style)
  - [Flow Style](#flow-style)
- [YAML Mapping](#yaml-mapping)
  - [Simple Mapping](#simple-mapping)
  - [Sequence in a Mapping](#sequence-in-a-mapping)
  - [Nested Mapping](#nested-mapping)
  - [Mixed mapping](#mixed-mapping)
- [YAML Sequences](#yaml-sequences)
- [YAML Scalars](#yaml-scalars)
- [YAML Structure](#yaml-structure)
- [YAML Comments](#yaml-comments)
- [YAML Anchors](#yaml-anchors)
- [YAML Tags](#yaml-tags)
  - [Set a URI:](#set-a-uri)
    - [Syntax](#syntax)
  - [Set a Local Tag](#set-a-local-tag)
  - [Set Datatype](#set-datatype)

## What is a YAML used for?

YAML is often used for configuration files that are parsed and read by a programming language or framework. Its human-readable format makes it easy for developers and system administrators to understand and modify configuration settings.

Here are some of the most common use cases for YAML:

- **Configuration management (CM)** – Ansible uses yaml files to describe all CM configurations (playbooks, roles, etc.).
- **Infrastructure as code (IaC)** – [OpenTofu](https://opentofu.org), for example, can read yaml files and use them as input for different resources, data sources, and even outputs.
- **CI/CD** – Many CI/CD products rely on yaml to describe their pipelines ([GitHub Actions](https://github.com/features/actions), [GitLab CI/CD](https://docs.gitlab.com/ee/ci), [Azure DevOps](https://azure.microsoft.com/en-us/products/devops), [CircleCI](https://circleci.com))
- **Container orchestration (CO)** – [K8s](https://kubernetes.io) and [Docker Compose](https://docs.docker.com/compose) rely heavily on yaml files to describe the infrastructure resources.
- **Data serialization** – YAML can be used to describe complex data types such as lists, maps, and objects.
- **APIs** – YAML can be used in defining API contracts and specifications (e.g. [OpenAPI](https://spec.openapis.org/oas/latest.html))

```yaml
# A sample yaml file
name: learning-yaml
domain:
  - devops
  - devsecops
tutorial:
  - yaml:
      name: "YAML Ain't Markup Language"
      type: awesome
      born: 2001
  - json:
      name: JavaScript Object Notation
      type: great
      born: 2001
  - xml:
      name: Extensible Markup Language
      type: good
      born: 1996
author: noyonalways
published: true
```

---

# Basic YAML Syntax

A YAML format primarily uses three node types:

1. **Maps/Dictionaries:** - (YAML calls it mapping) The content of a mapping node is an unordered set of key/value node pairs, with the restriction that each of the keys is unique. YAML places no further restrictions on the nodes.
2. **Arrays/Lists::** - (YAML calls them sequences) The content of a sequence node is an ordered series of zero or more nodes. In particular, a sequence may contain the same node more than once. It could even contain itself.
3. **Literals:** (Strings, numbers, boolean, etc.) The content of a scalar node is an opaque datum that can be presented as a series of zero or more Unicode characters.

| Character | Functionality                                   |
| --------- | ----------------------------------------------- |
| :         | It is used to describe the mapping value.       |
| -         | It describes the entry of the block sequence.   |
| '         | It describes the entry of flow collection.      |
| ?         | It is used to describe the mapping key.         |
| !         | It describes the tag a node                     |
| &         | It describes the anchor property of a node      |
| #         | It is used to describe the comments             |
| >         | It is used to describe the folded block scalar. |
| {         | It is used to start the mapping of flow         |
| }         | t is used to end the mapping of flow.           |
| [         | It is used to start the sequence of flow        |
| ]         | It is used to end the sequence of flow          |
| %         | It describes the use of directives.             |
| \*        | It is used to describe the alias node.          |

---

# YAML Data types

YAML has three types of data types:

- Scalar
- List
- Dictionary

## Scalar data type:

Scalar is a simple data type. In YAML, scalar means a simple value for a key. The value of the scalar can be integer, float, Boolean, and string. Scalar data types are classified into two data types:

1. Numeric Data type
2. String

### Numeric Data type

There are three types of numeric data type:

- Integer
- Floating point numbers
- Booleans

1. An **Integer data type** can be decimal, octal, or hexadecimal.

For example:

```yaml
age: 12345
octalexample: 012345
hexaexample: 0x12d4
```

Here, the hex value is indicated by 0x, and octal value is indicated by leading zero. When we run this document on our python script, the following output will be generated:

```yaml
age: 12345
octalexample: 9946
hexaexample: 4820
```

2. The **Floating-point value** can be fixed and exponential

For example:

```yaml
height: 180.0
exp: 12.3015e+05
```

When we evaluate the above entity, we will get the following:

```yaml
height: 180.0
exp: 1230150.0
```

3. A **Boolean value** can be True/False or Yes/No or On/Off.

For example:

```yaml
boolenval1: True
booleanval2: False
fan: On
light: Off
```

### String

YAML strings are Unicode. In the following example, we are going to define a simple string, without using quotes.

Example:

```yaml
str1: this is a normal string
```

When we process this, the following output will be generated:

```yaml
str1: this is a normal string
```

Now, we will define a string with an escape sequence. The following string contains a special character (anything other than alphanumeric), so it contains double-quotes.

```yaml
str1: "the cost is 390\n"
str2: the cost is 390\n
```

When we process this, the following output will be generated:

```yaml
str1: the cost is 390
str2: the cost is 390\n
```

During the YAML file, we can set the value of a data variable to be null. Later, we can write a program to change the value of null to any other value.

```yaml
str1: null
str2: ~
```

Our program processes this as:

```yaml
str1: none
str2: none
```

> In YAML, we can write a multi-line string in a single line using > symbol. In this, a newline character(\n) will be ignored.

Example:

```yaml
str: >
  this is a multi-line string it  
  spans more than one  
  line
```

The above string will interpret without the new lines as follows:

```yaml
str: this is a multi-line string it spans more than one line
```

> In YAML, we can write multi-line string in a newline using | symbol. In this, the newline character(\n) will be included.

Example:

```yaml
str: |
  this is a multi-line string it  
  spans more than one  
  line
```

So we see the new lines where they are in the document as follows:

```yaml
str : this is a multi-line string it
spans more than one
line
```

## Lists:

We can define the list in a single line as follows:

```yaml
items: [6, 7, 8, 9, 10]
name: [six, seven, eight, nine, ten]
```

This style is known as block style. We can put the above list in multiple lines as follows:

```yaml
items:
  - 6
  - 7
  - 8
name:
  - "six"
  - "seven"
  - "eight"
  - "nine"
```

This style is known as flow style. A list that contains complex objects needs multiple lines.

```yaml
items:
  - values:
      value1:
      value2:
      value3:
  - other values:
      key: value
```

> Any number of valid YAML values can contain by an array. But the value of a list can't be the same type.

## Dictionaries

If we want to write a complex YAML file which holds the complex data structure, we will use dictionaries. It is a collection of key: value pairs and each of the key: value pairs can be nested with a lot of options.

Example 1:

```yaml
student1: "noyon"
hobbies:
  - music
  - reading
  - traveling
```

In the above example, student is the first key, and john is the value. Hobbies are the second key, but it is nested, which means it contains a list of values. The value of the key can again be a key: value pair, which we will see in the next example.

Example 2:

```yaml
student2:
  fatherName: "William"
  motherName: "Marry"
  subjectDetails:
    subject1: 70
    subject2: 100
```

The subjectDetails shows a key, and the value of this key is a list of key: value pairs. fatherName, motherName, and subjectName are the keys. Where subjectName key contains a list of key: value pairs and subject1 and subject2 are the keys for values 70 and 100.

---

# YAML Styles

There are two types of styles in which we can write the YAML.

- Block styles
- Flow styles

## Block Style

We previously had seen the block style. Block style is less compact and better for humans. Traditional YAML makes it easy for humans to look at
the file, scan it down, and see what's going on.

Example

```yaml
name: Noyon Rahman
info:
  location: Gazipur
  age: 21
languages:
  - JavaScript
  - TypeScript
  - Python
```

In the above example, the first line shows a **key-value mapping**. Here, we use a colon for key-value pairs. The key is `name`, and the value is **Noyon Rahman**. The second line shows a **key-value mapping indentation**. It has an indentation under the **info**. The two values under `info` are part of `info` mapping. They are associated with each other because they have two space indents before the actual key that is `location` and `age`. The `languages` key shows a **list indentation**. It has indentation because it has a list under the `languages`. It contains the dashes to indicate that it is a list, not just a key-value.

## Flow Style

Flow style is an extension of JSON. It is used to allow YAML and JSON to work together. Flow style is less human-readable, but sometimes they are better for the computer that processing our YAML. Flow style is used to fold the long line of content.

Example

```yaml
name: Noyon Rahman
info: { location: Gazipur, age: 21 }
languages: [JavaScript, TypeScript, Python]
```

Instead of sub-line our `location` and `age` information into indent lines under the `info` key, we have a set of curly brackets, and we define our key: value pairs in those brackets. Similarly, we define an array into a square bracket. It also allows a different use of tag and anchors in our YAML, which we define later.

---

# YAML Mapping

In this section, we will write proper YAML. YAML mappings are also known as associative arrays, hash tables, key: value pairs, or collection. In mapping, the name of two keys can't be the same. There are four types of mapping:

- Simple mapping
- Sequence mapping
- Nested mapping
- Mixed mapping

## Simple Mapping

In simple mapping, we will provide a key in the first part, and then separate with a colon and space. It is necessary to use a space. We will put each member of the list on a new line if we want to add a keyed list(dictionary) on our document, in this example, we have a host key, and the host's value is phl-42. We also have a key student, and the name of student is harry.

Example:

```yaml
repo: learning-yaml
student: noyon
```

In a single key: value mapping, we will change the above YAML into flow style. So we will use double quotes to show the value of key. When we evaluate the above YAML example in python, we will get the following:

```yaml
repo: "learning-yaml"
student: "noyon"
```

## Sequence in a Mapping

We can map the value of the key in sequence. In the following example, we have a key languages and a list under languages. It contains the dashes to indicate that it is a list, not just a key-value.

Example

```yaml
student: noyon
languages:
  - JavaScript
  - TypeScript
  - Python
```

In sequence key: value mapping, we will change the above YAML into flow style. So we have to use square brackets to show the list of languages, and we also have to use commas between all languages. We will add all these in a single line. When we evaluate the above example, we will get the following:

```yaml
student: "noyon"
languages: [JavaScript, TypeScript, Python]
```

## Nested Mapping

We can nest our mapping within each other. In the following example, we have a key info, and under info we have three key: value pairs. The first one is location for the value Gazipur. The second one is age for value 21. The third one is email for value noyonrahman@gmail.com.

```yaml
name: Noyon Rahman
info:
  location: Gazipur
  age: 21
  email: noyonrahman@gmail.com
```

In the nested key: value mapping, we will change the above YAML into flow style. So we have to use curly brackets, and we also have to use commas between our additional values. We will add all these in a single line as follows:

```yaml
name: "Noyon Rahman"
info: { location: Gazipur, age: 21, email: noyonrahman@gmail.com }
```

## Mixed mapping

In mixed mapping, we have an assortment of mapping and sequences as values.

Example

```yaml
student: Noyon Rahman
details:
  email: noyonrahman2003@gmail.com
  phone: +88017********
more:
  - subject1
  - subject2
```

When we evaluate the above YAML example, we will get the following:

```yaml
student1: "Noyon Rahman"
details: { email: noyonrahman2003@gmail.com, phone: +88017******** }
more: [subject1, subject2]
```

---

# YAML Sequences

In this section, we are going to discuss sequences. Sequences can also be known as lists, arrays.

Along with mapping, YAML can also be considered as a collection. In YAML, the collection is represented with proper sequence styles.

Example 1:

```yaml
roles:
  - frontend
  - backend
```

The first example shows the collection. It contains a list under roles.

Example 2:

```yaml
host: Noyon Rahman
info:
  location: Gazipur
  age: 21
  phone: +88017********
```

The info mapping, location, age, and phone are also a collection. So, if something indented and all indented together at the same work, this is considered a single collection. So, we have terminology that defines that how list within YAML works.

If we see a list in YAML, they will probably be combined with mapping. So, we will discuss the **mapping of sequences**. The mapping of sequences works if at the end of our file of example 2, we provide roles then we provide anything under roles in list form. This process is known as the mapping of sequences.

Example 3:

```yaml
host-php-42
datacenter:
  location: canada
  cab: 13
  cab_unit: 3
roles:
  - webserver
  - wp_database
```

In the above example, we have roles. Now assume that host-php-42 is a webserver and that webserver has wp_database(Wordpress database). So, we have two roles here, the webserver and the wp_database.

If we have a mapping of sequences, we also have a sequence of mappings or even a sequence of sequences. So, if we want to see the sequence of mapping, we will adapt our location, cab, and cab_unit in this. Instead of starting two spaces before the location, we will first apply a dash and a single space before the location. Similar to key: value pairs, space is non-optional. So, we have dash and space, and under that, we have a list of mapping. There are also other ways to provide sequences.

Sequences can't be blank, and they also can't be nested without mapping. The following example shows what we should not do in YAML:

```yaml
- playbooks
  - wordpress
  -
  - mysql
```

The above example has a list of playbooks. But this list has a lack of colon. The colon is missing, that's why we will not be able to run this YAML file. We also would not able to use it because our second item is completely blank. If we want to consider the second blank item, we have to add two quotes, which are shown as follows:

```yaml
- playbooks
  - wordpress
  - ""
  - mysql
```

Similar to mapping, we also have an option to provide a flow style version of a sequence. So, if we want to adapt roles into flow style, instead of using curly brackets around them, we will use square brackets. We have to provide a comma in between our two values. We also have to remove the brackets and bring it all up on the same line. So, we are going to convert example 1 into flow style as follows:

```yaml
roles: [webserver, wp_database]
```

In this file, we actually write a pretty typical YAML file using just two basic YAML features: mapping, sequences, and combination of mapping and sequences.

---

# YAML Scalars

In this section, we are going to discuss about scalars. We already learned mapping and sequences. While using mapping and sequences, we already used scalars. Scalars are a string, a number, or Boolean. White space is permitted in YAML.

Example 1:

```yaml
host: php-42
datacenter:
  location: Las Vegas
  cab: 13
  cab_unit: 3
```

In the above example, Las Vegas is valid, just like Canada. We don't need to put Las Vegas in quotes to make it a string.

We will use single quotes or double quotes to convert a non-sting scalar into a string scalar. In example 1, the values 13 and 3 are plain numbers. They are not considered strings. But it is possible to convert these numbers into strings. We can either use single quotes around them or double quotes around them to convert them into strings.

Example 2:

```yaml
host: php-42
datacenter:
  location: Canada
  cab: "13"
  cab_unit: "3"
```

The difference between single quotes and double quotes is double quotes allow **escape sequences**.

Example 3:

```yaml
host: php-42
datacenter:
  location: Canada
  cab: "13\n"
  cab_unit: '3\n'
```

When we process the above example:

```yaml
host: php-42
datacenter:
  location: Canada
  cab: 13
  cab_unit: 3\n
```

That means double quotes consider **\n** as a new line, and single quotes consider it as a normal text. Scalars mean one individual piece of content. So the location key itself a scalar, Canada value itself also a scalar. So mapping is essentially used to assign one scalar to another.

If we want to add a value that happens to be longer and need to spend across multiple lines, there are two different symbols which allow for multiple lines. The first one is |, and the second one is >.

In YAML, we can write a multi-line string in a newline using | symbol. In this, the newline character(\n) will be **included**.

Example 4:

```yaml
downtime_sch: |
  2019-07-29 - kernel upgrade  
  2020-05-12 - security fix
```

In the above example, we have a downtime_sch key, and then we have a | symbol, which indicates that it is going to be multiple lines. Now under that, we have a date for a kernel upgrade in the first line, and we have a date for security fix in the second line. When we process the above example, we will see the new lines where they are in the document as follows:

```yaml
downtime_sch:
2019-07-29 - kernel upgrade
2020-05-12 - security fix
```

In YAML, we can write a multi-line string in a single line using > symbol. In this, a newline character(\n) will be **ignored**.

Example 5:

```yaml
comments: >
  Experiencing high I/O  
  since 2019-04-29.  
  Currently investigating
```

We have a comment line, and then we have a >(closing angular brackets). Now under that, we can type any comment that we want. We have written Experiencing high I/O in the first line, since 2019-04-29 in the second line, and Currently investigating in the third line. When we process the above example, it will interpret without the new lines as follows

```yaml
comments: Experiencing high I/O since 2019-04-29. Currently investigating
```

During the YAML file, we can set the value of a data variable to be null. Later, we can write a program to change the value of null to any other value.

```yaml
str1: null
str2: ~
```

Our program processes this as follows:

```yaml
str1: none
str2: none
```

---

# YAML Structure

In YAML, we can add multiple directives or documents in a single file. Before we do that, we are going to add some additional structural options. So while using a YAML if we want to know the start of a file, we will supply three initial dashes at the top of a file.

Example:

```yaml
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
```

For these single directives or a single document file, these three dashes are optional. If we are creating multiple document streams, these three dashes are mandatory. There are two ways where we can use these triple dashes.

In the above example, we have our host information for phl-42, but what if we want to add another Philadelphia host i.e., phl-43. So instead of creating a second host of YAML file, we will actually add three more dashes at the end of the above YAML file. After these three dashes, we can continue on to supply the additional host information.

```yaml
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
---
host: phl-43
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "4"
```

So now we have phl-43. Now we can supply our datacenter information. Under that, we added location, cab and cab_unit as Philadelphia, 13, and this time the cab_unit is 4. Three dashes separate our directives.

We can keep doing this for as long as we need. If we want to go ahead and add one more host information about Philadelphia i.e., phl-44. We can keep going and adding our documents and directives.

```yaml
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
---
host: phl-43
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "4"
---
host: phl-44
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "5"
```

Now we add all the data that we want to add. Beyond just triple dashes, we also have the option to use triple dotes. Now, beyond just applying information about our Philadelphia host, we also want to add information about our Helsinka host.

When we add three dots in place of three dashes, these three dots will provide the signal about the end of this directive or this entire collection by closing the data stream. So after three dots, we are actually adding three dashes to open up another document and then we supply additional information that is necessary directly related to our Philadelphia host, but we will add in the end of the information that we are supplying.

```yaml
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
---
host: phl-43
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "4"
---
host: hel-13
datacenter:
  location: Helsinka
  cab: "9"
  cab_unit: "2"
```

So instead of supplying the information of our Philadelphia host, we will supply the information about Helsinka host 13, i.e., hel-13. Now we can go ahead and supply whatever information we want to add. So we add datacenter, and under that we add location, cab, and cab_unit as Helsinka, 9, and 2.

Now we can keep going and adding Helsinka host many time we need it or we can go ahead and end the stream with three dots.

```yaml
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
---
host: phl-43
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "4"
---
host: hel-13
datacenter:
  location: Helsinka
  cab: "9"
  cab_unit: "2"
---
host: hel-14
datacenter:
  location: Helsinka
  cab: "9"
  cab_unit: "1"
```

In the above example, we add one more information about Helsinka host i.e., hel-14, and end the stream with three dots.

Often we are using YAML, especially for configuration and configurations files, we notice that the three dashes and three dots separators are entirely optional.

---

# YAML Comments

If we are familiar with any coding language, data serialization language, or programming language, we know why we talk about comments yet. In YAML, Commenting works in Splash and many other languages.

At the comment, we have to add an octothorpe or a hashtag and a whitespace. Whitespace means a space, a tab, or any spacing between the octothorpe and actual comments. Comments can be placed on their own line. So, we are going to add Philly DC Host Data at the top of the file.

Example:

```yaml
# Philly DC Host Data
---
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
roles:
  - webserver
  - wp_database
```

We can also add inline comments, so we are going to supply the reference id or reference name of Philadelphia, i.e., PHL at the end of Philadelphia. When we add an inline comment, they do have to come at the end of the line. We cannot add any more information about our location here. Because once we add the octothorpe, everything that comes after that is just for us. Whenever human opens the file and take a look at the file, which goes to show us that any information we add to comments should just be for the humans reading. No actual information that a computer is going to need or need to be processed should be added after an octothorpe. The example of the inline comment is as follows:s

Example

```yaml
# Philly DC Host Data
---
host: phl-42
datacenter:
  location: Philadelphia # Reference ID: PHL
  cab: "13"
  cab_unit: "3"
roles:
  - webserver
  - wp_database
```

One more thing we are going to discuss is blank lines. The example of a blank line is as follows:

```yaml
# Philly DC Host Data
---
host: phl-42
datacenter:
  location: Philadelphia # Reference ID: PHL
  #
  cab: "13"
  cab_unit: "3"
roles:
  - webserver
  - wp_database
```

The space between location and cab is just going to be written as a comment. It is not going to particular interrupt anything.

There are wrong ways to use comments, which we are going to understand using the two examples.

Example 1:

```yaml
#Philly DC Host Data
---
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
```

When we see the above example, we can see that the issue is that there is no actual space between the octothorpe and the comment. So when the user is processing our YAML, it is going to know that this is a comment and infect it's more likely that we are going to experience an error with that "after octothorpe no space Philly DC Host Data".

Example 2:

```yaml
#Philly DC Host Data
---
host: phl-42
datacenter:
  location: "Philadelphia #
Reference ID: PHL"
  cab: "13"
  cab_unit: "3"
```

In the above example, if we look at our location data, we do have an octothorpe there, and it does continue to the end, but since for whatever reason, our Philadelphia value is quoted. So the inline comment is going to be included in the quoted string. So there are some easier mistakes we can make while commenting.

---

# YAML Anchors

In this section, we are going to learn how to utilize Anchors. It allows us to store and reuse data within our YAML file. When we enter data into our YAML file, we might find that some data or an entire collection of data gets reused throughout the file, as shown below:

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: ! PHL Philadelphia
  cab: !!str 13
  cab_unit: !!str 3
roles:
  - webserver
  - wp_database
---
host: phl-43
datacenter:
  location: ! PHL Philadelphia
  cab: !!str 13
  cab_unit: !!str 4
```

In the above example, the Philadelphia location and roles are reused in the phl-42 host and phl-43 host. Instead of copying and pasting all of the same roles into every single server that serves our word press host. We can set an anchor that will put in all of the roles of the word press host, and then automatically add them into any line that contains the reference anchor.

Let's go ahead and write some of this to see action. So if we want to set up an anchor, instead of trying to type our Philadelphia location every time, we reference Philadelphia in our PHL and our full datacenters. We will substitute the plain old tag, as shown in example 1, and replace the exclamation point(!) with the end(&) symbol. The & symbol is used to set an anchor. So later we go to the bottom of our phl-43 host data, and remove the location where we have manually typed the name Philadelphia and just reference our Philadelphia line with astrict(\*) PHL, as shown in the following example:

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: &PHL Philadelphia
  cab: !!str 13
  cab_unit: !!str 3
roles:
  - webserver
  - wp_database
---
host: phl-43
datacenter:
  location: *PHL
  cab: !!str 13
  cab_unit: !!str 4
```

However, we don't have to limit ourselves to our anchor referencing a single line. So we will go back to the example of roles. Where we have our roles information, i.e., this is a web server and word press database. So it is safe to assume that this is a word press host. So we want to set a tag so that every word press host can use these roles. So after the colon and a white space, we add & symbol and then wphost in line with the roles data. We can also add &wphost on the next line of a role. Either way, this is going to put everything in this collection of the webserver and wp_database information.

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: &PHL Philadelphia
  cab: !!str 13
  cab_unit: !!str 3
roles: &wphost
  - webserver
  - wp_database
---
host: phl-43
datacenter:
  location: *PHL
  cab: !!str 13
  cab_unit: !!str 4
```

In the above example, we don't have any roles added to the second host definition, i.e., **phl-43**. So if we go ahead and add our roles file and if whatever reason our **phl-43** host forwards the same information as our **phl-42** host, then we can go ahead and reference this with just \***wphost**. Now when the data is parsed, it is going to put in the **webserver** and **wp_database** list from the instance of the **wphost anchor**.

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: &PHL Philadelphia
  cab: !!str 13
  cab_unit: !!str 3
roles: &wphost
  - webserver
  - wp_database
---
host: phl-43
datacenter:
  location: *PHL
  cab: !!str 13
  cab_unit: !!str 4
roles: *wphost
```

In the above example, we will notice when using this, i.e., if we reuse the name of the **anchor** later on the file, it will work in the same way as we are using a **variable** in most programming languages. It will reassign the value of that anchor to whatever the **new value** is.

If we assign **&PHL** tag to **phl-43** host, the location under **phl-43** host is not going to be the **Philadelphia** from the instance at the top. It is going to be the same as the host key that is **phl-43**.

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: &PHL Philadelphia
  cab: !!str 13
  cab_unit: !!str 3
roles: &wphost
  - webserver
  - wp_database
---
host: &PHL phl-43
datacenter:
  location: *PHL
  cab: !!str 13
  cab_unit: !!str 4
roles: *wphost
```

---

# YAML Tags

In this section, we are going to learn how to use tags within our YAML files. So tags can use one of three purposes within a YAML file that is described below:

- We can utilize tags to set a custom URI (universal resource indicator), which is used to reference our tags.
- We can also use them to set local tags. Local tag is a tag that is relevant only to the existing YAML file. If we include a local tag in the body of our file, that tag will also be tagged on to the end of a universal resource indicator (URI).
- We can also use tags to set the data type. In the previous examples, we can manually set the cab and cab_unit using quotation marks.

## Set a URI:

We don't need these URI tags for any configuration management or just configuration file settings that were using YAML. However, if we are using YAML as a data store for an application we are creating, the URI tags are useful. URI tags are useful if we use conjunction or JYAML or whatever YAML API is available with our programming language. The custom URI that we want to set ends up in the metadata area of our host file or any YAML file. So the URI will set above our three-dot start document indicators. We first define a URI tag by adding the % (percent sign) and Tag indicator, and then we can go ahead and add an exclamation point (!), which is going to work as a prefix to the local tag.

### Syntax

```yaml
%TAG ! prefix
```

Now we set the prefix to our URI. In this case, we will set our prefix as tag:hostsdata:phl: described below:

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: Philadelphia
  cab: "13"
  cab_unit: "3"
roles:
  - webserver
  - wp_database
```

## Set a Local Tag

Now we go ahead and set a local tag to our document. To do this, we are using the Philadelphia location. We assign the exclamation point(!) and PHP tag before Philadelphia, which denotes that we are working in location Philadelphia. Now when we reference this, we will call it tag:hostsdata:phl:PHL. That's all we will do to set a local tag, and then we will be able to reference the tag.

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: ! PHL Philadelphia
  cab: "13"
  cab_unit: "3"
roles:
  - webserver
  - wp_database
```

## Set Datatype

We can also utilize a tag to change the functionality of how are parser read our YAML. Now we set our cab and cab_unit to string without using quotes because YAML does not involve quotes (""). Using tags, we can change the data type. To do this, we will use two exclamation points(!!), after that, we go ahead and set our data type, which in this case is str means string. We can also change it into different data types like sequence, mapping, etc. When we are working in a specific language like Python, Ruby, then that language or that program has an additional set of data type tags we can reference.

```yaml
%TAG ! tag:hostsdata:phl:
---
host: phl-42
datacenter:
  location: ! PHL Philadelphia
  cab: !!str 13
  cab_unit: !!str 3
roles:
  - webserver
  - wp_database
```
