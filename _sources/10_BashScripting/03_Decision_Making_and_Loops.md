# Decision Making and Loops

## User Input

- Before going to see how to write decision statements in bash scripting, lets first see how to read an input from the user in bash scripting.

- In bash scripting, if we want to read an input from bash scripting then we use `read` statement.

  **Syntax** : `read <variable_name>`

  **Ex** : `read SKILL`

  Once this statement gets executed, then it asks for the user prompt (or input). Once user entered the input and hit enter, then that value or data gets stored in that variable and we can access that data from that variable.

  There are some options with `read` statement.

  1. `-p` : It is used to display some prompt for user when they are entering the input.

     **Ex** : `read -p "Enter the Username: " USERNAME`

  2. `-s` : It will suppress the input we are entering. That means if you are entering some input, then it won't be visible to the user. This would be mostly used in password mechanism.

     **Ex** : `read -sp "Enter Password: " PASS`

## Decision Statements

- Decision Statements are used to run or execute particular commands when there are set of conditions satisfied. To achieve this in bash scripting, we use the `if-else` or `if-elif-else` statements.

- If you are checking only single condition then we can use the following syntax.

  ```bash

  if [ $VAR <Operator> <operand> ]
  then

     <commands>

  else

     <commands>

  fi

  ```

- Sample example for single condition checking is:

  ```bash

  #!/bin/bash

  read -p "Enter a Number: " NUM

  if [ $NUM -gt 100 ]
  then

     echo "The number you entered is greater than 100"

  else

     echo "The number you entered is less than 100"

  fi

- If you are checking multiple conditions, then we have to use the following syntax.

  ```bash

  if [ $VAR <operator> <operand> ]
  then

     <commands>

  elif [ $VAR <operator> <operand> ]
  then

     <commands>

  else

     <commands>

  fi

  ```

- Sample Example for this is:

  ```bash 

  #!/bin/bash

  VALUE=$(ip addr show | grep -v LOOPBACK | grep -ic mtu)

  if [ $VALUE -eq 1 ]
  then
      echo "1 Active Network Interface Found"

  elif [ $VALUE -gt 1]
  then
      echo "Multiple Active Network Interfaces Found"

  else

     echo "No active network interfaces found."

  fi

  ```

## Loops

- To perform single task reptitively in bash, we actually need to use the loops. There are actually two kinds of loops. One is `for` loop and another one is while loop.

- Syntax of `for` loop is:

  ```bash
  #!/bin/bash

  for <variable> in <sequence>
  do
     <commands>
  done

  ```

- Example of `for` loop is 

  ```bash
  #!/bin/bash

  numbers="one two three"

  for Var in $numbers
  do
     echo "Looping ... "
     echo $Var
  done

  ``` 

- Syntax of `while` loop is 

  ```bash

  #!/bin/bash

  while [ <condition> ]
  do
    <commands>
  done

  ```

- Example for `while` loop is 

  ```bash

  #!/bin/bash

  counter=0

  while [ $counter -le 5 ]
  do
    echo "Looping..."
    echo $counter
    counter=$(( $counter + 1 ))
  done

  ```