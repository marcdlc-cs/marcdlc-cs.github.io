---
title: Using Python for File Updates
permalink: /python1
parent: Python
---
# Using Python for File Updates
{: .no_toc }

{: .note }
Incident Investigation, Data Analysis, Security Event Monitoring, Basic SQL Proficiency
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I'm a cybersecurity professional at a healthcare company. My role involves regularly updating a file that lists employees with access to restricted content, particularly those working with personal patient records. Access to this content is controlled by IP addresses, with an allow list specifying authorized IP addresses for the restricted subnetwork. Additionally, there's a remove list that identifies employees to be removed from the allow list.

My project entails developing a Python algorithm to check whether the allow list includes any IP addresses found on the remove list. If such IPs are present, I must remove them from the allow list file.

## Goals & Objectives
Create an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list. If so, you should remove those IP addresses from the file containing the allow list.

## Results
### 📄 Task 1: Open the file that contains the allow list

```python
import_file = "allow_list.txt"
# Open the allow list using a with statement
with open(import_file, "r") as file:
```

{: .note2 }
> The text file that contains a list of IP addresses of authorized employees is called “allow_list.txt.” I store it as a string in variable called “import_file.”
>
>To open that file, I use a with statement and the open() function that takes two arguements: the file to be opened, and “r” which indicates that I want to read the file. The final portion of the with statement “as file” stores the contents of “allow_list.txt” in a variable called “file.”

<br>
<br>
### 📄 Task 2: Read the file contents

```python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
    # Use the .read() method on the file variable to convert its contents into a string
    ip_addresses = file.read()
```

{: .note2 }
To make it easier to the parse the data in the allow list, I use the .read() method on the file variable to convert its contents into a string. This string of data is then stored in a variable called “ip_addresses.” I can then use this string data in my Python program.

<br>
<br>
### 📄 Task 3: Convert the string into a list

```python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
    ip_addresses = file.read()
# Use the .split() method on ip_addresses to convert its string data into a list
ip_addresses = ip_addresses.split()
```

{: .note2 }
Before I can start to remove unauthorized IP addresses from the allow list, I must first convert the string data contained in ip_addresses into a list. I use the .split() method to accomplish this. By default, the .split() function splits the text by whitespace into list elements.

<br>
<br>
### 📄 Task 4: Iterate through the remove list

```python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
    ip_addresses = file.read()
ip_addresses = ip_addresses.split()

# Unauthorized IP addresses that must be removed from the allow list
remove_list = ['192.168.1.10', '10.0.0.5', '172.16.0.1', '192.168.2.15', '192.168.0.2']

# Use a for loop to apply specific code statements to all elements remove_list
for element in remove_list:
```

{: .note2 }
>A list of unauthorized IP addresses that must be removed from ip_addresses is contained in the variable “remove_list” A for loop header is prepared so that the list can be iterated through. In the for loop header, “for” designates that this is a looping function, “element” represents each item in the list of unauthorized IP addresses, and “in remove_lists” tells Python that the list elements to be looped through are contained in the variable “remove_list.”
>
>The for loop in Python repeats code for a specified sequence. The overall purpose of the for loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. 

<br>
<br>
### 📄 Task 5: Remove IP addresses that are on the remove list

```python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
    ip_addresses = file.read()
ip_addresses = ip_addresses.split()

remove_list = ['192.168.1.10', '10.0.0.5', '172.16.0.1', '192.168.2.15', '192.168.0.2']

for element in remove_list:
    # Use an if statement to check if an IP address in the remove list is present in the allow list
	if element in ip_addresses:
        # If the condition above is true, remove that IP address from the allow list
		ip_addresses.remove(element)
```

{: .note2 }
>I need to check if an unauthorized IP addresses is present in the ip_addresses list. If so, then that IP address must be removed from ip_addresses. To accomplish this, I use an if statement that executes code if a statement is true. In the if statement header, “element in allow_list” is the condition that must be true; that condition is: an element in remove_list is present in ip_addresses. If that is true, then the next line of code is executed. The .remove() method removes that element from the ip_addresses list, effectively updating it.
>
>❗In this scenario, there are no duplicates in the ip_addresses list, so using .remove() in this way is appropriate.

<br>
<br>
### 📄 Task 7: Update the file with the revised list of IP addresses 

```python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
    ip_addresses = file.read()
ip_addresses = ip_addresses.split()

remove_list = ['192.168.1.10', '10.0.0.5', '172.16.0.1', '192.168.2.15', '192.168.0.2']

for element in remove_list:
	if element in ip_addresses:
		ip_addresses.remove(element)

# Convert ip_addresses back into a string so that it can be written into the text file
ip_addresses = "\n".join(ip_addresses)
# Use a with statemnt to write over the original file
with open(import_file, "w") as file:
    # Rewrite the file, replacing its contents with ip_addresses
	file.write(ip_addresses)
```

{: .note2 }
With the ip_addresses list updated, I can now update the original file “allow_list.txt.” First, I must convert ip_addresses back into a string using the .join() method. “\n” formats the string so that each element is on a new line. The argument passed into the .join() method is the name of the list that must be converted. Using with and .open( ), I pass in “import_file” (the variable that contains allow_list.txt) and “w” which indicates that I want to write over the file. Using the .write() method on the “file” variable and passing ip_addresses into it, I am able to update allow_list.txt with the updated string data from ip_addresses.

<br>
<br>
### Summary

Using this algorithm, I was able to update the file that contains all authorized IP addresses that are able to access the restricted subnetwork. The ```write``` statement, ```.open()``` and ```.read()``` function allowed me to access the contents of allow_list.txt and convert it into a string. After converting that string into a list using the ```.split()``` method, I was able to iterate over it and remove unauthorized IP addresses. Finally, the ```.join()``` method converts the list back into a string. Using ```with```, that string data was then used to update allow_list.txt.