# Update a file through a Python algorithm

### Project description

At an organization, access to restricted content is controlled with an allow list of IP addresses. The `"allow_list.txt"` file identifies these IP addresses. A separate remove list identifies IP addresses that should no longer have access to this content. Lets create an algorithm to automate updating the `"allow_list.txt"` file and remove these IP addresses that should no longer have access. 

## Open the file that contains the allow list
For the first part of the algorithm, open the `"allow_list.txt"` file. First, assign this file name as a string to the `import_file` variable:

```python
# Assign 'import_file' to the name of the file

import_file = "allow_list.txt"
```

Then, use a `with` statement to open the file:

```python
# Build 'with' statement to read in the initial contents of the file

with open(import_file, "r") as file:
```

In this algorithm, the `with` statement is used with the `.open()` function in read mode to open the allow list file for reading. The purpose of opening the file is to allow access to the stored IP addresses. The `with` keyword will help manage the resources by closing the file after exiting the `with` statement. In the code `with open(import_file, "r") as file:`, the `open()` function has two parameters. The first identifies the file to import, and then the second indicates what we want to do with the file. In this case, `"r"` indicates we want to read it. The code also uses the `as` keyword to assign a variable named `file`; `file` stores the output of the `.open()` function while we work within the `with` statement.

## Read the file contents
In order to read the file contents, use the `.read()` method to convert it into the string.

```python
with open(import_file, "r") as file:

  # Use '.read()' to read the imported file and store it in a variable named 'ip_addresses'

  ip_addresses = file.read()
```

When using an `.open()` function that includes the argument `"r"`, we can call the `.read()` function in the body of the `with` statement. The `.read()` method converts the file into a string. Apply the `.read()` method to the `file` variable identified in the `with` statement. Then, assign the string output of this method to the variable `ip_addresses`. 

In summary, this code reads the contents of the `"allow_list.txt"` file into a string format that allows us to later use the string to organize and extract data in the Python program.

## Convert the string into a list

In order to remove individual IP addresses from the allow list, we needed it to be in list format. Use the `.split()` method to convert the `ip_addresses` string into a list:

```python
# Use '.split()' to convert 'ip_addresses' from a string to a list

ip_addresses = ip_addresses.split()
```

The `.split()` function is called by appending it to a string variable. It works by converting the contents of a string to a list. The purpose of splitting `ip_addresses` into a list is to make it easier to remove IP addresses from the allow list. By default, the `.split()` function splits the text by whitespace into list elements. In this algorithm, the `.split()` function takes the data stored in the variable `ip_addresses`, which is a string of IP addresses that are each separated by whitespace, and it converts this string into a list of IP addresses. To store this list, reassign it back to the variable `ip_addresses`. 


## Iterate through the remove list
A key part of the algorithm involves iterating through the IP addresses that are elements in the `remove_list`. To do this, lets incorporate a for loop:

```python
# Build iterative statement
# Name loop variable 'element'
# Loop through 'remove_list'

for element in remove_list:
```

The `for` loop in Python repeats code for a specified sequence. The overall purpose of the `for` loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. The `for` keyword starts the `for` loop. It is followed by the loop variable `element` and the keyword `in`. The keyword `in` indicates to iterate through the sequence `ip_addresses` and assign each value to the loop variable `element`. 

## Remove IP addresses that are on the remove list

This algorithm requires removing any IP address from the allow list, `ip_addresses`, that are reflected in `remove_list`.  Because there were not any duplicates in `ip_addresses`, we are able to use the following code to do this:

```python
for element in remove_list:

  # Create conditional statement to evaluate if 'element' is in 'ip_address'

    if element in ip_addresses:

    # use the '.remove()' method to remove elements from 'ip_addresses'

      ip_addresses.remove(element)
```



First, within the `for` loop, create a conditional that evaluates whether or not the loop variable `element` was found in the `ip_addresses` list. Applying `.remove()` to elements that were not found in `ip_addresses` would result in an error. 

Then, within that conditional, apply `.remove()` to `ip_addresses`. Pass in the loop variable `element` as the argument so that each IP address that was in the `remove_list` would be removed from `ip_addresses`.

## Update the file with the revised list of IP addresses 

As a final step in the algorithm, we need to update the allow list file with the revised list of IP addresses. To do so, first convert the list back into a string. Use the `.join()` method for this:

```python
# Convert 'ip_addresses' back to a string so that it can be written into the text file

ip_addresses = "\n".join(ip_addresses) 
```

The `.join()` method combines all items in an iterable into a string. The `.join()` method is applied to a string containing characters that will separate the elements in the iterable once joined into a string. We used the `.join()` method to create a string from the list `ip_addresses`, we can pass it in as an argument to the `.write()` method when writing to the file `"allow_list.txt"`. Use the string `("\n")` as the separator to instruct Python to place each element on a new line. 

Then, use another `with` statement and the `.write()` method to update the file:

```python
# build 'with' statement to rewrite the original file

with open(import_file, "w") as file:

  # Rewrite the file, replacing its contents with 'ip_addresses'

  file.write(ip_addresses)
```

This time, we used a second argument of `"w"` with the `open()` function in the `with` statement. This argument indicates to open a file and write over its contents. When using this argument `"w"`, we can call the `.write()` function in the body of the `with` statement. The `.write()` function writes string data to a specified file and replaces any existing file content. 

In this case we seek to write the updated allow list as a string to the file `"allow_list.txt"`. This way, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list. To rewrite the file, we appended the `.write()` function to the file object file identified in the with statement. We passed in the `ip_addresses` variable as the argument to specify that the contents of the file specified in the with statement should be replaced with the data in this variable.

## Summary

We created an algorithm that removes IP addresses identified in a `remove_list` variable from the `"allow_list.txt"` file of approved IP addresses. This algorithm involved opening the file, converting it to a string to be read, and then converting this string to a list stored in the variable `ip_addresses`. we then iterated through the IP addresses in `remove_list`. With each iteration, evaluated if the element was part of the `ip_addresses` list. If it was, we applied the `.remove()` method to it, removing the element from `ip_addresses`.. After this, we used the `.join()` method to convert the `ip_addresses` back into a string to write over the contents of the `"allow_list.txt"` file with the new and revised list of IPs.

---
*Google's cybersecurity: Automating Cybersecurity tasks with Python*
