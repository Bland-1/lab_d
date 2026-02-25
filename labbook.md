
Q1

In the .h file, you must provide the declaration (or prototype) of the constructor or method inside the class definition.

In the .cpp file, you must provide the implementation (or definition) of the constructor or method. To do this, you must #include the corresponding header file and use the class name followed by the scope resolution operator (::) before the method name (e.g., Grid::Grid()) to link the code back to the class.


Q2

<img width="933" height="936" alt="image" src="https://github.com/user-attachments/assets/d1fdb30e-4cca-420c-8760-035242a9d2fc" />

1.	File Stream Creation: An std::ifstream object is created using the provided filename parameter, opening the file for reading.
2.	Nested Loop Structure: 2 nested for loops iterate through all 81 cells of the grid:
The outer loop iterates through y-coordinates (rows) from 0 to 8
The inner loop iterates through x-coordinates (columns) from 0 to 8

4.	Data Reading: The extraction operator (>>) reads integer values sequentially from the input file stream into m_grid[x][y], filling the array in row-major order (left to right, top to bottom).
5.	File Closure: After all values are read, the close() method explicitly closes the file stream to release the file resource.


Q3

void Grid::SaveGrid(const char filename[])
{
	std::ofstream outputFile(filename);
	for (int y = 0; y <= 8; y++)
	{
		for (int x = 0; x <= 8; x++)
		{
			outputFile << m_grid[x][y];
			if (x < 8)
				outputFile << " "; 
		}
		outputFile << std::endl;  
	}
	outputFile.close();
}

Uses std::ofstream to write to file
Mirrors the nested loop structure from LoadGrid (y outer, x inner) to maintain consistent indexing
Writes each value with space separation (except after the last column)
Adds newline after each row for readability
Output file will be "OutGrid.txt" (as shown in the commented code in main)

Q4

#include <iostream>
using namespace std;

void functionA() {
	int a = 10;
	int b = 20;
	int *p = &a;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;

	*p = 100;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
}

void functionB() {
	int a = 10;
	int b = 20;
	int c = 30;
	int *p = &b;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	cout << "c= " << c << endl;

	*p = 100;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	cout << "c= " << c << endl;
} 


void functionC() {
	unsigned int a = 0x00ff00ff;
	unsigned int *p = (unsigned int *)a;

	*p = 999;
}

void functionD() {
	double x = 3.14;

	cout << "x= " << x << endl;

	// Add code here

	cout << "x= " << x << endl;
}

int main(int, char**) {

	functionA();
	//functionB();
	//functionC();
	//functionD();

	return 0;
}

<img width="1729" height="900" alt="image" src="https://github.com/user-attachments/assets/43bae539-8def-41d7-a31e-8036e9797982" />




Q5

#include <iostream>
using namespace std;

void functionA() {
	int a = 10;
	int b = 20;
	int *p = &a;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;

	*p = 100;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
}

void functionB() {
	int a = 10;
	int b = 20;
	int c = 30;
	int *p = &b;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	cout << "c= " << c << endl;
	
	*p = 100;
	p++;
	*p = 200;

	cout << "a= " << a << endl;
	cout << "b= " << b << endl;
	cout << "c= " << c << endl;
} 

void functionC() {
	unsigned int a = 0x00ff00ff;
	unsigned int *p = (unsigned int *)a;

	*p = 999;
}

void functionD() {
	double x = 3.14;

	cout << "x= " << x << endl;

	// Add code here

	cout << "x= " << x << endl;
}

int main(int, char**) {

	//functionA();
	functionB();
	//functionC();
	//functionD();

	return 0;
}

This caused stack coruption when completing 


Q6

programe crashed as windows does not let the user have access to change that part of the systems memory

Q7

void functionD() {
	double x = 3.14;

	cout << "x= " << x << endl;

	double *q = &x;
	double **p = &q;

	**p = 2.71828;

	// Add code here

	cout << "x= " << x << endl;
}

q is a pointer to double that stores the address of x
p is a pointer to pointer-to-double (double **) that stores the address of q
To access x through p, we use double dereferencing (**p):
*p gives us the value stored in p, which is the address stored in q (address of x)
**p gives us the value at that address, which is x itself
