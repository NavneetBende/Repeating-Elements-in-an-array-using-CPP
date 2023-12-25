Find Repeating Elements In An Array  in C++
Here, in this page we will discuss the program to print the repeating elements in an array in C++ programming language. We are given with an array and need to print the repeated elements of the array. We will discuss two different methods to print them.

Repeating elements in an array in Cpp
Here, in this page we will discuss two different methods to print the repeated elements of the given input array. These two methods are :

Method 1 : Using loops
Method 2 : Using Map.
Method 3 : Using Sorting
Method 1 :
In this method we will count the frequency of each elements using two for loops.

To check the status of visited elements create a array of size n.
Run a loop from index 0 to n and check if (visited[i]==1) then skip that element.
Otherwise create a variable count = 1 to keep the count of frequency.
Run a loop from index i+1 to n
Check if(arr[i]==arr[j]), then increment the count by 1 and set visited[j]=1.
After complete iteration of inner for loop check if(count!=1), then print that element.
Time and Space Complexity :
Time Complexity : O(n2)
Space Complexity : O(n)
Method 1 : Code in C++
Run
Run
#include <bits/stdc++.h>
using namespace std;

// Main function to run the program
int main() 
{ 
    int arr[] = {10, 30, 10, 20, 40, 20, 50, 10}; 
    int n = sizeof(arr)/sizeof(arr[0]); 

    int visited[n];

    for(int i=0; i<n; i++){

        if(visited[i]!=1){
           int count = 1;
           for(int j=i+1; j<n; j++){
              if(arr[i]==arr[j]){
                 count++;
                 visited[j]=1;
              }
            }
            if(count!=1)
             cout<<arr[i]<<" ";
         }
     }
    
    return 0; 
}
Output :
10 20
Related Pages
Finding the Longest Palindrome in an Array

Counting Distinct Elements in an Array

Finding Non Repeating elements in an Array

Removing Duplicate elements from an array

Finding Minimum scalar product of two vectors

Method 2 :
In this method we will use hash-map to store the frequency of the elements and print those elements whose frequency is not equals to 1.

Create an unordered_map say mp and a variable say count_dis=0 to count the unique elements.
Run a loop to iterate over array
Set mp[arr[i]]++
After, complete iteration, run a loop over map
Check if value != 1, then print that key value.
Time and Space Complexity :
Time Complexity : O(n)
Space Complexity : O(n)
Repeated elements in C++
Method 2 : Code in C++
Run

#include <bits/stdc++.h>
using namespace std;

// Main function to run the program
int main() 
{ 
   int arr[] = {10, 30, 40, 20, 10, 20, 40, 10}; 
   int n = sizeof(arr)/sizeof(arr[0]); 

   unordered_map <int, int>mp;
   int count_dis=0;

   for(int i=0; i<n; i++) mp[arr[i]]++; 
   for(auto it=mp.begin(); it!=mp.end(); it++)
{ 
        if(it->second!=1) cout<<it->first<<" ";
   }
}
Output :
20 40 10
Method 3 :
The previous method uses extra O(N) space for the visited array, which is undesirable.

We can do the following technique but we have to make sure that the array is sorted. We will use a sorting algorithm to sort the array

We have used bubble sort(Time complexity: O(N^2). But you can use Merge Sort or Quick Sort, which will reduce the sorting time complexity to O(n log(n))

Method 3 : Code in C++
Run
#include<bits/stdc++.h>
using namespace std;

// using bubble sort to sort the array
int bubbleSort(int arr[], int size){

    for (int i = 0; i < size-1; i++){ 
         // Since, after each iteration righmost i elements are sorted 
         for (int j = 0; j < size-i-1; j++) if (arr[j] > arr[j+1]){
                int temp = arr[j]; // swap the element
                arr[j] = arr[j+1]; 
                arr[j+1] = temp; 
             }
    }
    return 0;
}

// find repeating element
void findRepeating(int arr[], int n){

    int count = 0;

    for (int i = 0; i < n; i++) {

       int flag = 0;
       while (i < n - 1 && arr[i] == arr[i + 1]){
             flag = 1;
             i++;
       }
       if(flag)
          cout<<arr[i-1]<<" ";
    }

}

// Main function to run the program
int main() 
{ 
    int arr[] = {20, 30, 10, 2, 10, 20, 30, 11}; 
    int n = sizeof(arr)/sizeof(arr[0]);

    bubbleSort(arr, n);

    findRepeating(arr, n);

    return 0; 
}
// Time Complexity : O(N)
// Space Complexity : O(1)
Output :
10 20 30
