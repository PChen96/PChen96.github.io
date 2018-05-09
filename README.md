## Welcome to GitHub Pages

### Lab1

```markdown

//Author: Phillip Chen
//Course: {135,136}
//Instructor: Alexey Nikolaev
//Assignment: Lab 1 - Task B

//the example uses the time from the computer and compares it to the sunset time you set
//if the computer time is before sunset time itll say good afternoon
//if the computer time is after sunset time itll say good evening


#include <iostream>
#include <ctime>
using namespace std;

int main () {

	time_t t;
	struct tm *now;
	t = time(0);             // get current time                                          
	now = localtime(&t);     // adjust for local timezone
	int hour = now->tm_hour; // retrieve current hours
	int min = now->tm_min;   // retrieve current minutes
	
	//input hours when it is sun set
	cout << "Enter the hours part of today's sunset time (4-9):" <<endl;
	int sunset_hour = 0;
	cin >> sunset_hour;
	sunset_hour = sunset_hour + 12; // add 12 to the variable, you can also do; sunset_hour += 12
	
	//input minutes when it is sun set
	cout << "Enter the minutes part of today's sunset time (0-59):" <<endl;
	int sunset_min;
	cin >> sunset_min;
	
	//hellos
	if (hour < 12 ) {
		cout << "Good Morning" << endl;
	}
	else {
		int total_cur_min = hour * 60 + min ;//converting computer time to minutes
		int total_sunset_min = sunset_hour * 60 + sunset_min ;//converting set sunset time to minutes
		//cout << total_cur_min << endl; this is here to help me see behind the scenes what the numbers are
		//cout << total_sunset_min << endl;
		
		if (total_sunset_min > total_cur_min){
			cout<<"Good Afternoon" <<endl;
			}
		else{
			cout<<"Good Evening"<<endl;
			
		}
	}
}

```
```markdown

//Author: Phillip Chen
//Course: {135,136}
//Instructor: Alexey Nikolaev
//Assignment: Lab 1 - Task C

//This program says good morning if the computer time is before noon (12)or
//good afternoon or good evening depending on the time you set for sunset
//it will also calculate when you'll arrive home when you provide commute time

#include <iostream>
#include <ctime>
using namespace std;

int main () {

	time_t t;
	struct tm *now;
	t = time(0);             // get current time                                          
	now = localtime(&t);     // adjust for local timezone
	int hour = now->tm_hour; // retrieve current hours
	int min = now->tm_min;   // retrieve current minutes
	
	//input hours when it is sun set
	cout << "Enter the hours part of today's sunset time (4-9):" <<endl;
	int sunset_hour = 0;
	cin >> sunset_hour;
	sunset_hour = sunset_hour + 12; // add 12 to the variable, you can also do; sunset_hour += 12
	
	//input minutes when it is sun set
	cout << "Enter the minutes part of today's sunset time (0-59):" <<endl;
	int sunset_min;
	cin >> sunset_min;
	
	//hellos
	if (hour < 12 ) {
		cout << "Good Morning" << endl;
	}
	else {
		int total_cur_min = hour * 60 + min ;//converting computer time to minutes
		int total_sunset_min = sunset_hour * 60 + sunset_min ;//converting set sunset time to minutes
		if (total_sunset_min > total_cur_min){// if computer time less than sunset time its afternoon
			cout<<"Good Afternoon" <<endl;//12-sunset time
			}
		else{
			cout<<"Good Evening"<<endl;// else ( means its more ) will be evening, sunset time to midnight
			
		}
	}
	//part c
	cout << "How many minutes from now do you expect to be home?"<<endl;
	int travel_min_hourless = 0; // make a variable to hold minutes after %
	int travel_min = 0;//variable to hold minutes 
	int travel_hour = 0;
	cin >> travel_min;
	travel_min = travel_min + min;
	
	if (travel_min + min > 60){
		travel_min_hourless = travel_min % 60;/// made sure to save travel_min to different variable to use it for next equation  
		travel_hour =travel_min / 60;/// these two equation uses same variable 
		cout << "You will get home at " << hour+travel_hour << ":" << travel_min_hourless << endl;

	}
	else{
		cout << "You will get home at " << hour << ":" << travel_min + min << endl;
	}
}
// the example uses the time from the computer and compares it to the sunset time you set
// if the computer time is before sunset time itll say good afternoon
// if the computer time is after sunset time itll say good evening
```
### Lab 2
```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 2 task A

Input a number from 1 - 20, program will request you to re-enter a number if you input wrong number
after inputing a numbber from 1-20, it will raise 2 to that power
*/

#include <iostream>
using namespace std;

int main()
{
	cout << "Please enter n" << endl;//input a number between 1 to 20
	int n = 0;
	cin >> n;
	
	while ((n < 1) || (n > 20) ) //error checking the input to see if it is 1 - 20
	{	cout << "Please re-enter" << endl;
		cin >> n;
	}
	
	int total = 1; //2^0
	for(int e = 1; e <= n; e++)
	{
		total = total*2;
		cout << total << endl;
	}
}
		
```

```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 2 task B

Using the verhulst Formula. After entering number, decimal, decimal, number, number.
The loop function will give you the population for each year
*/

#include <iostream>
using namespace std;

int main()
{
	double p0 = 0; //population
	double g = 0; //growth rate
	double h = 0; //death rate
	double M = 0; //Maximum capacity
	int y = 0; //years
	
	cout << "Enter the initial population (p0)" << endl;
	cin >> p0;
	while (p0 < 0) //error checking, we need p0 a positive number
	{
		 cout << "Please re-enter" << endl;
		 cin >> p0;
	}
	
	cout << "Enter the groth rate (g)" << endl;
	cin >> g;
	while (g < 0) //error checking, we need g a positive number
	{
		 cout << "Please re-enter" << endl;
		 cin >> g;
	}
	
	cout << "Enter the death rate (h)" << endl;
	cin >> h;
	while (h < 0) //error checking, we need h a positive number
	{
		 cout << "Please re-enter" << endl;
		 cin >> h;
	}
	
	cout << "Enter the maximum capacity (M)" << endl;
	cin >> M;
	
	while (M < 0) //error checking, we need p0 a positive number
	{
		 cout << "Please re-enter" << endl;
		 cin >> M;
	}
	
	cout << "Enter the number of years to simulate (years):";
	cin >> y;
	
	cout << "0	" << p0 << endl;
	for(int i=1; i<=y ; i++)
	{
		p0 = p0 + (g * p0) - (h * p0) - (g * (p0*p0)/M);
		cout << i << "	" << p0 << endl;
	}
	
}
```
###lab3
```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 3 task A

Input 2 numbers for height and weight. The program will then use loop code to print out a 
hallow rectangle based on the measurements you input.
*/
#include <iostream>
using namespace std;

int main(){

int w = 0;
int h = 0;

do{
	cout<<"Input weight: ";
	cin>>w;
	}while(w<=0);

do{
	cout<<"Input height: ";
	cin>>h;
	}while(h<=0);

for (int i=0; i<w;i++){		//this make the top of the square
	cout<<"*";}
	
cout<<endl;					//this makes the print start at the next line

for(int i=0;i<(h-2);i++){		//if the height is greater than 1 then it prints more
	cout<<"*";
	for(int a=0;a<(w-2);a++){
		cout<<" ";
		}
	cout<<"*"<<endl;
	}
	
for (int i=0; i<w;i++){		//this make the bottom of the square
	cout<<"*";}

cout<<endl;	
}

```

```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 3 task B

Ask for 1 input. Then prints out a right triangle with input as height
*/

#include <iostream>
using namespace std;

int main(){

int s=0;
do{
	cout<<"Input side length: ";
	cin>>s;}while(s<=0);

for(int i=0;i<s;i++){
	for(int a=-1;i>a ;a++){
	cout<<"*";}
	cout<<endl;}
}
```

```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 3 task c

Ask for 2 inputs. Then creates a trapeoid with width as a base 
and growings rows above depending on the your height input.
*/

#include <iostream>
using namespace std;

int main(){

int w = 0;
int h = 0;

do{
	cout<<"Input width: ";
	cin>>w;
	}while(w<=0);

do{
	cout<<"Input height: ";
	cin>>h;
	}while(h<=0);

for(int i=0; i<h;i++){				//sets the boundary of how many rows 
	for(int a=0;a<=(w-h)+i;a++){	//constructs the pattern for trapeoid
	cout<<"*";}
	cout<<endl;
	}
}
```

```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 3 task d

Ask for 1 input and outputs a right triangle with it's right located at the top right
of print screen
*/

#include <iostream>
using namespace std;

int main(){

int s = 0;
do{
	cout<<"Input side length: ";
	cin>>s;}while(s<=0);

for (int i=0; i<s;i++){			//how many rows repeated
	int b=0; b++;				//another counter
	for(int a=1; a-i<b;a++){	//fills in the spaces in rows
		cout<<" ";}
	for(int c=0; c+i<s;c++){	//fills in the * in rows
		cout<<"*";}
	cout<<endl;
	}
}
```

```markdowm
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 3 task e

Ask for one input (diameter). Using the circle formula. if you subtract
the center point with the x and y axis you will get negative numbers
but that wouldnt matter because the circle formula square these numbers
making them positive; x*x + y*y < r*r
the code says greater than because that line put in the empty spaces
outside of the circle
*/

#include <iostream>
using namespace std;

int main(){

double d = 0;
do{
	cout<<"Input diameter: ";
	cin>>d;}while(d<=0);

double r = d/2;			//radius
double c = (d-1)/2;		//center of circle; given in lab notes

for(double y=0; y<d;y++){
	for(double x=0; x<d;x++){	//left to right x axis
		if((y-c)*(y-c)+(x-c)*(x-c)>r*r){
					cout<<" ";
					/*cout<<"rounded"<<rounded;
					cout<<"x"<<x<<endl;*/
							
				}
				else{
				cout<<"*";
				}				
			}cout<<endl;
		
		}

}
			
```
### Jekyll Themes


### Support or Contact
