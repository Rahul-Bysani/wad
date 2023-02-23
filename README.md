Ex 3. Demonstrate the usage of colab notebook and perform the task
Colaboratory, or “Colab” for short, is a product from Google Research. Colab allows
anybody to write and execute arbitrary python code through the browser. Google Colab
is a free cloud-based service that allows the execution of Python code using the Jupyter
Notebook format. It is possible to use and install new python libraries. Colab notebooks
are stored in Google Drive, or can be loaded from GitHub. Colab notebooks can be
shared just as you would with Google Docs or Sheets. Simply click the Share button at
the top right of any Colab notebook, or follow these Google Drive file sharing
instructions.
Procedure:
1. Go to google colab
2. On the left top corner, open file new notebook start writing the code 



3a. Python code to perform Selectin Sort:
def selection_sort(array):
 length = len(array)

 for i in range(length-1):
 minIndex = i

 for j in range(i+1, length):
 if array[j]<array[minIndex]:
 minIndex = j

 array[i], array[minIndex] = array[minIndex], array[i]


 return array
array = [21,6,9,33,3]

print("The sorted array is: ", selection_sort(array)) 




3b. Python code to check whether the given number is Armstrong or not
# Python program to check if the number is an Armstrong number or not
# take input from the user
num = int(input("Enter a number: "))
# initialize sum
sum = 0
# find the sum of the cube of each digit
temp = num
while temp > 0:
 digit = temp % 10
 sum += digit ** 3
 temp //= 10
# display the result
if num == sum:
 print(num,"is an Armstrong number")
else:
 print(num,"is not an Armstrong number")
 
 
 
 
 
 
 
 
 
 
 
 # Function to convert integer to Roman values
def printRoman(number):
 num = [1, 4, 5, 9, 10, 40, 50, 90,
 100, 400, 500, 900, 1000]
 sym = ["I", "IV", "V", "IX", "X", "XL",
 "L", "XC", "C", "CD", "D", "CM", "M"]
 i = 12

 while number:
 div = number // num[i]
 number %= num[i]

 while div:
 print(sym[i], end = "")
 div -= 1
 i -= 1

# Driver code
if __name__ == "__main__":
 number = 3549
 print("Roman value is:", end = " ")
 printRoman(number)
 
 
 
 
 Ex 4. Demonstrate the usage of cloudsim using NetBeans
Cloudsim: It is an open-source framework, which is used to simulate cloud
computing infrastructure and services. It is developed by the CLOUDS Lab
organization and is written entirely in Java. It is used for evaluating a hypothesis prior
to software development in order to reproduce tests and results.
For example, if you were to deploy an application or a website on the cloud and
wanted to test the services and load that your product can handle and also tune its
performance to overcome bottlenecks before risking deployment, then such
evaluations could be performed by simply coding a simulation of that environment
with the help of various flexible and scalable classes provided by the Cloud Sim
package, free of cost.
Explanation of the program:
In the below given program we are trying to use cloud simulator and create 2 virtual
machines( VM#0 and VM#1) and allocate 2 data centres( Datacenter#2) for the
created virtual machines and after creation successful message, after some time it
will destroys the created VM#0 and VM#1.
The output of this program gives the information about the status of the code,
execution time and Id of VM and datacentre respectively
Procedure:
1. Visit the website cloudbus.org on the internet
2. Download the simulator known as “clodsim 3.0.3”
3. Extract the zip file, the downloaded zip file contains folders namely- docs,
examples, jars and sources
4. using the NetBeans 7.2 software, create a new project of a java applications
and name it as “myapp”
5. Now, under the properties of that particular(“myapp”) project select
libraries and add jar folder
6. Browse folders in the system to find the downloaded cloudsim folder and
add cloudsim- jars- cloudsim-3.0.3 and click open (add -jar files)
7. Copy the code present in the cloudsim folder under cloudsim-exampleexample1 and paste it on NetBeans
DAYANANDA SAGAR COLLEGE OF ENGINEERING
13
1. (Path: cloudsim3.0.3\examples\org\cloudbus\cloudsim\examples)
8. Take care while changing default package and class name, keep the package
name and class name as per your project name and instance file name as per
your program. (Change the package name and class name)
9. Run the program and note the output in a table format from the output
section of NetBeans 





