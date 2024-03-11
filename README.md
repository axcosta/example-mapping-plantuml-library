# Example Mapping Diagram with PlantUML

This is a really simple library to aid creation of Example Mapping diagrams with PlantUML. Notation is derived from seminal work by Matt Wyne in ["Introducing Example Mapping"](https://cucumber.io/blog/bdd/example-mapping-introduction).

## Getting Started

To get started, include the `ExampleMappingCommon.puml` file from the `dist` directory in each `.puml` file or PlantUML diagram. This can be referenced by a URL directly to this repository, or by including the file locally.

### Using this repository

This references the latest _GitHub release_ version of the referenced file from GitHub when an Internet connection is available. It is recommended _not_ to use the `main` branch, but instead a specific release version. The example below references the current _0.1.0_ release.

```c
!include https://raw.githubusercontent.com/axcosta/example-mapping-plantuml-library/0.1.0/ExampleMappingCommon.puml
```

You can also define the URL and include de definition:

```c
!define ExampleMappingPuml https://raw.githubusercontent.com/axcosta/example-mapping-plantuml-library/0.1.0
!include ExampleMappingPuml/ExampleMappingCommon.puml
```

### Including the file locally

```c
!include path/to/ExampleMappingCommon.puml
```

## Example Mapping Diagram

### Objects

These are the objects that can be defined:

- UserStory
- Rule
- Example
- Question

### Demonstration

Below, there is the [examples/ProcessFreeShipping.puml](examples/ProcessFreeShipping.puml) diagram code:

```c
@startuml Process Free Shipping (examples/ProcessFreeShipping.puml) 

!define ExampleMappingPuml https://raw.githubusercontent.com/axcosta/example-mapping-plantuml-library/main/ExampleMappingCommon.puml
!include ExampleMappingPuml/ExampleMappingCommon.puml

left to right direction

title Process Free Shipping from [[https://draft.io/example/example-mapping]]

UserStory("Process Free Shipping", "Give free shipping based on certain conditions") {
  Question("What if customer lives in France?")
  Question("What if customer wants a fast delivery?")
  Question("What if customer uses fidelity points?")
  Rule("Free shipping from $25 with certain category of products") {
    Example("Free shipping from $25 picture closed to concerned products")
  }
  Rule("Free shipping marketing banner in product page") {
    Example("Show banner when limit is not reached")
    Example("Showcase free shipping when limit is exceeded")
  }
  Rule("Minimum of $50 in Shopping Cart") {
    Example("Greater than $50 items get free delivery")
    Example("All products are allowed in shopping cart")
    Example("Show shipping costs while the limit is not reached")
  }    
}

@enduml
```

This code generates the following diagram:

![Example Mapping Demo](http://www.plantuml.com/plantuml/proxy?idx=0&src=https://raw.githubusercontent.com/axcosta/example-mapping-plantuml-library/main/examples/ProcessFreeShipping.puml)

### Custom configuration

You can customize this library by setting the following variables in your Plant UML file:

| Variable | Description | Default value
| ---------|-------------|----------
| default_text_alignment | Text alignment of objects labels and descriptions | `left`
| default_user_story_color | Background color of User Story object (see [PlantUML colors](https://plantuml.com/color>)) | `Business`
| default_rule_color | Background color of Rule object (see [PlantUML colors](https://plantuml.com/color>))| `LightBlue`
| default_example_color | Background color of Example object (see [PlantUML colors](https://plantuml.com/color>))| `YellowGreen`
| default_question_color | Background color of Question object (see [PlantUML colors](https://plantuml.com/color>)) | `LightPink`
| default_description_font_size | Font size of object description | `12`
| default_spacing | Spacing between object label and description | `"\n\n"`
| default_max_characters_per_line | Maximum characters per line for object labels and descriptions (this only applies when variable `limit_max_characters_per_line` is equal to `true`) | `30`
| limit_max_characters_per_line | Enable/Disable limit of maxixum characters per line | `"true"`
| show_map_stereotypes | Enable/Disable showing of object stereotypes | `"false"`
| log_enabled | Enable/Disable logging (for debug purposes) | `"false"`

For example, for showing the objects stereotypes in your diagram, set in your code (remember to include `!$` in the beggining of variable definition):

```c
!$show_map_stereotypes = "true"
```
