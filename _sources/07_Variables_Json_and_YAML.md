# Variables, Json and YAML

## Variables

- In Bash Scripting Variables are nothing but the temporary storage of data. If you open any terminal such as Git Bash etc, we can create variables normally as we have created in python. But those variables are in memeroy until gitbash is open. Whenever git bash gets closed those variables gets deleted from memory. To create a variable in Terminal we jsut follow this syntax.

  **Syntax** : `<Variable_Name> = <Data_Value>`

  **Ex** : `skill = "Devops"

  Whenever are declaring variables we shouldn't put space between `=` sign and variable ame and data values. There should be no space between them

- Inorder to print the variables in terminals we generally use `echo` command. `echo` is similar to print statement in python. Whatever data you given as input it would print same.

  **Ex** : `echo Hii` -> Hii (Here we doesn't need double or single quotes to display it)

  If we want to display the variable we will a `$` (dollar) symbol in front of variable.

  **Ex** : `echo $skill` -> Devops

  If you want to display so text along with variable then we should use the double quotes not single quotes. If you use single quotes it will print same content you kept in between single quotes.

  **Ex** : `echo "I have learned $skill` -> I have learned Devops

  **Ex** : `echo 'I have learned $skill'` -> I have learned $skill

## JSON

- JSON stands for JavaScript Object Notation. It is a lightweight data interchange format, that is easy for machines to parse and generate. It is originally derived from javascript, it is now language independent and widel used in web APIs and data transfer.

- A simple example of writing JSON is :

  ```json
  {
    "Name" : "Sai",
    "Age" : 45,
    "Skills" : ["Devops", "Data Engineering", "Big Data"],
    "IsGraduated" : True
  }
  ```

- Json is strict, machine readable , Easy to parse and widely used in data exchange in APIs.

## YAML

- YAML stands for YAML Ain't Markup Language or we generally call it as Yet Anothor Markup Language. It is a human-readable data serialization format, designed to be cleaner and more intuitive to read and write by humans.

- A simple example for YAML is

  ```yaml

    Name : Sai
    Age : 45
    Skills : 
        - Devops
        - Data Engineering
        - Big Data

    isGraduated : True

  ```
- YAML is Minimal and clean, highly readable, Friendly for writing config files, supports complex features like anchors and references

- YAML was introduced to solve limitations in JSON which are Verbose with brackets and commas, No Comments Allowed, Quotes required on strings, Hard to write nested structures. YAML solves this by introducing clean and indentation-based format, supports inline and block comments, quotes are optional unless needed, easy indentation to represent hierarichy and soon.

