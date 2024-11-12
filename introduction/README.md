# YAML - Introduction

YAML is one of the most popular data [`serialization languages`](https://devopedia.org/data-serialization), and it is used mostly for writing configuration files. The YAML recursive acronym stands for YAML Ain’t Markup Language. This language is designed with flexibility and accessibility in mind, so it’s human-readable and simple to understand. YAML works with all modern programming languages and is widely used in data persistence, internet messaging, cross-language data sharing, and many other places. YAML files either have the extension .yaml or .yml.

All of these factors contribute to YAML’s popularity as a configuration language in the DevOps domain, where it is widely used with well-known tools such as Kubernetes, Ansible, and Terraform.

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
