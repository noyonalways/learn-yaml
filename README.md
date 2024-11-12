<img style="border-radius: 8px" width="100%" src="https://i.ibb.co.com/R6CFG73/yaml-github-banner.png" alt="learning-yaml-banner-image"/>

# YAML - Introduction

YAML is one of the most popular data [`serialization languages`](https://devopedia.org/data-serialization), and it is used mostly for writing configuration files. The YAML recursive acronym stands for YAML Ain’t Markup Language. This language is designed with flexibility and accessibility in mind, so it’s human-readable and simple to understand. YAML works with all modern programming languages and is widely used in data persistence, internet messaging, cross-language data sharing, and many other places. YAML files either have the extension .yaml or .yml.

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

## What is a YAML used for?

YAML is often used for configuration files that are parsed and read by a programming language or framework. Its human-readable format makes it easy for developers and system administrators to understand and modify configuration settings.

Here are some of the most common use cases for YAML:

- **Configuration management (CM)** – Ansible uses yaml files to describe all CM configurations (playbooks, roles, etc.).
- **Infrastructure as code (IaC)** – OpenTofu, for example, can read yaml files and use them as input for different resources, data sources, and even outputs.
- **CI/CD** – Many CI/CD products rely on yaml to describe their pipelines (GitHub Actions, GitLab CI/CD, Azure DevOps, CircleCI)
- **Container orchestration (CO)** – K8s and Docker Compose rely heavily on yaml files to describe the infrastructure resources.
- **Data serialization** – YAML can be used to describe complex data types such as lists, maps, and objects.
- **APIs** – YAML can be used in defining API contracts and specifications (e.g. OpenAPI)

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
