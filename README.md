## Welcome to GitHub Pages

### Lab1

```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: Alexey Nikolaev
Assignment: Lab 1 - Task B

the example uses the time from the computer and compares it to the sunset time you set
if the computer time is before sunset time itll say good afternoon
if the computer time is after sunset time itll say good evening
*/

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
/*
Author: Phillip Chen
Course: {135,136}
Instructor: Alexey Nikolaev
Assignment: Lab 1 - Task C

This program says good morning if the computer time is before noon (12)or
good afternoon or good evening depending on the time you set for sunset
it will also calculate when you'll arrive home when you provide commute time
*/

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
### Lab3
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
### Lab 4
```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 4 task A

Input two integars to computer C(n,k)
overflows at C(13,1)
*/
#include <iostream>
using namespace std;

int main(){

int n = 0;
int k = 0;
int producta = 1;
int productb = 1;
int productc = 1;
int finalprod = 1;

cout<<"input n: ";
cin>>n;

cout<<"input k: ";
cin>>k;

	for (int factor = 1; factor<= n; factor++) 
		{
		producta = producta * factor;
		//cout<<"n: "<<producta<<'\t'<<"factor: "<<factor<<endl;
		}
	for (int factor = 1; factor<= k; factor++) 
		{
		productb = productb * factor;
		//cout<<"k: "<<productb<<'\t'<<"factor: "<<factor<<endl;
		}
	for (int factor = 1; factor<= n-k; factor++) 
		{
		productc = productc * factor;
		//cout<<"n-k: "<<productc<<'\t'<<"factor: "<<factor<<endl;
		}
	finalprod = producta/(productb*productc);

cout<<"C("<<n<<","<<k<<"): "<<finalprod<<endl;
}
```

```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 4 task B

user inputs two intergers to compute C(n,k)
Allows the user to compute k <= n/2
if you attemp to plug in a k >n/2 you'll get the wrong answer
*/
#include <iostream>
using namespace std;

int main(){

int n = 0;
int k = 0;
int producta = 1;
int productb = 1;
int finalprod = 1;

cout<<"input n: ";
cin>>n;

cout<<"input k: ";
cin>>k;

if (k <= n/2){ //removes (n-k)! in n!/[k!(n-k)!], computes n!/k!,computes small k
	for (int factor = n-k+1; factor<= n; factor++) 
		{
		producta = producta * factor;
		//cout<<"n "<<producta<<'\t'<<" factor: "<<factor<<endl;
		}
	for (int factor = 1; factor<= k; factor++) 
		{
		productb = productb * factor;
		//cout<<"k "<<productb<<'\t'<<" factor: "<<factor<<endl;
		}
	}
finalprod = producta/productb;
	
cout<<"C("<<n<<","<<k<<"): "<<finalprod<<endl;
}
```

```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 4 task C

user inputs two intergers to compute C(n,k)
Allows the user to compute k<= n/2 and k >n/2
*/
#include <iostream>
using namespace std;

int main(){

int n = 0;
int k = 0;
int producta = 1;
int productb = 1;
int finalprod = 1;

cout<<"input n: ";
cin>>n;

cout<<"input k: ";
cin>>k;

if (k <= n/2){ //removes (n-k)! in n!/[k!(n-k)!], computes n!/k!,computes small k
	for (int factor = n-k+1; factor<= n; factor++) 
		{
		producta = producta * factor;
		//cout<<"n "<<producta<<'\t'<<" factor: "<<factor<<endl;
		}
	for (int factor = 1; factor<= k; factor++) 
		{
		productb = productb * factor;
		//cout<<"k "<<productb<<'\t'<<" factor: "<<factor<<endl;
		}
	}
else{	//removes k! in n!/[k!(n-k)!] computes n!/(n-k)!, computes big k
	for (int factor = k+1; factor<= n; factor++) 
		{
		producta = producta * factor;
		//cout<<"n "<<producta<<'\t'<<" factor: "<<factor<<endl;
		}
	for (int factor = 1; factor<= n-k; factor++) 
		{
		productb = productb * factor;
		//cout<<"k "<<productb<<'\t'<<" factor: "<<factor<<endl;
		}
}
finalprod = producta/productb;
	
cout<<"C("<<n<<","<<k<<"): "<<finalprod<<endl;
}
```
```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: Lab 4 task D

Input two integars to compute C(n,k)
this program can compute larger values of n and k
*/
#include <iostream>
using namespace std;

int main(){

double n = 0;
double k = 0;
double producta = 1;
double productb = 1;

cout<<"input n: ";
cin>>n;

cout<<"input k: ";
cin>>k;

for(int i = 1; i < k+1; i++){
	producta=1+(n-k)/i;
	productb=producta*productb;
	//cout<<"productb :"<<productb<<'\t'<<"i: "<<i<<endl;
	}

cout<<"C("<<n<<","<<k<<"): "<<productb<<endl;
}
```
### Lab 5
```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: <Lab 5a

This program takes one input, a non negative number. It tells you how many digits long that digit with a function
*/

# include <iostream>
using namespace std;

int numDigit(int num){
	int counter = 0;
	while (num>=10){
		num = num/10;
		counter++;
	}
	counter=counter+1;
	return counter;
}

int main(){

	cout<<"Enter number: ";
	int num = 0;
	cin>>num;
		
	int result = numDigit(num);
	cout << result << endl;

}

```
```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: <Lab 5b

This program takes one input, a non negative number. It tells you how many digits long that digit with a function
*/

# include <iostream>
using namespace std;

int numDigit(int num){
	int counter = 0;
	while (num>=10){
		num = num/10;
		counter++;
	}
	counter=counter+1;
	return counter;
}

int getDigit(int num, int result, int index){
	for(int i=0;i<result-index+1;i++){	//5-2 of 12345 3
		if(i<result-index){
			num=num/10;
			}
		else{ num=num%10;
			  return num;
			}
		}
	}
int main(){

	cout<<"Enter number: ";
	int num = 0;
	cin>>num;
	cout<<"Enter index: ";
	int index = 0;
	cin>>index;

	int result=numDigit(num);

	int digit = getDigit(num,result,index);
	cout<<digit<<endl;
	

}
```
```markdown
/*
Author: Phillip Chen
Course: {135,136}
Instructor: <Alex Nikolaev
Assignment: <Lab 5b repeating

Reads your number to see if it is divisible by 9 and then changes the number to be divisible by 9
*/

# include <iostream>
using namespace std;

int numDigit(int ran){		//this function counts how many digits in number inputed
	int counter = 0;		//counter, this will be returned
	while (ran>=10){		//when ran >=10 divide 10 and repeat until 1 digit remains
		ran = ran/10;
		counter++;
	}
	counter=counter+1;		//counter records how many times loop repeated and adds 1 then returns
	return counter;
}

int getsum(int num, int result){
	int sum = 0;
	for(int k = 1; k <= result; k++)	//repeat until you take every digit in number
	{int ph=num;
		for(int i=0;i<result-k+1;i++)		//removing digits by itself
		{
			if(i<result-k){						//dividing you need is at one's place
				ph=ph/10;
			}
			else{ ph=ph%10;				//module to get the remainder getting the number by itself	
			  	sum=ph+sum;				//add the number gotten with previous sums
			}
		}
	}return sum;
}

void makeDivisibleByNine(int &num){
	int ph = num % 10;
	num=num-ph;
	while(num%9!=0)
	{num++;}
	}
	
int main(){

	cout<<"Enter number: ";
	int num = 0;
	cin>>num;

	int result=numDigit(num);
	int sum = 0;
	int digit = getsum(num,result);
	if(digit%9==0){					//this is to see if number inputed is divisible by 9
	cout<<num<<endl;				
	}
	else{							//if it is not divisible by 9, we change the number
	makeDivisibleByNine(num);
	cout<<num<<endl;
	}
}
```
### Lab 6 was a debug lab
### Lab 7
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 7 Task 1
  Description:
  
    The program reads a PGM image from the file "inImage.pgm",
    and outputs a modified image to "outImage.pgm". 
    Most code are from task 0 (code given),
    inserted code at 108-110 so that it outputs an inverse color image given
*/
#include <iostream>
#include <cassert>
#include <cstdlib>
#include <fstream>
using namespace std;

const int MAX_W = 512;
const int MAX_H = 512;

// reads a PGM file.
// Notice that: width and height are passed by reference!

void readImage(int image[MAX_W][MAX_H], int &width, int &height) {
	char c;
	int x;
	ifstream instr;
	instr.open("inImage.pgm");
	// read the header P2
	instr >> c;
	assert(c == 'P');
	instr >> c;
	assert(c == '2');
	// skip the comments (if any)
	while ((instr>>ws).peek() == '#') {
		instr.ignore(4096, '\n');
	}
	instr >> width;
	instr >> height;
	assert(width <= MAX_W);
	assert(height <= MAX_H);
	int max;
	instr >> max;
	assert(max == 255);
	for (int row = 0; row < height; row++)
		for (int col = 0; col < width; col++)
			instr >> image[col][row];
	instr.close();
	return;
}

// Writes a PGM file
void writeImage(int image[MAX_W][MAX_H], int width, int height) {
	ofstream ostr;
	ostr.open("outImage.pgm");
	if (ostr.fail()) {
		cout << "Unable to write file\n";
		exit(1);
	};

	// print the header
	ostr << "P2" << endl;
	// width, height
	ostr << width << ' ';
	ostr << height << endl;
	ostr << 255 << endl;
	for (int row = 0; row < height; row++) {
		for (int col = 0; col < width; col++) {
			assert(image[col][row] < 256);
			assert(image[col][row] >= 0);
			ostr << image[col][row] << ' ';
			// lines should be no longer than 70 characters
			if ((col+1)%16 == 0) ostr << endl;
		}
		ostr << endl;
	}
	ostr.close();
	return;
}

int main() {
	int img[MAX_W][MAX_H];
	int w, h;
	readImage(img, w, h); // read it from the file "inImage.pgm"
	// w and h were passed by reference and now contain the dimensions of the picture
	// and the 2-dimesional array img contains the image data
	// Now we can manipulate the image the way we like
	// for example we copy its contents into a new array
	//white is 255, black is 0
	int out[MAX_W][MAX_H];
	for(int x = 0; x < w; x++) {
		for(int y = 0; y < h; y++) {
			int c = img[x][y];
			c = (c-255)*-1;//we want to change 0 to 255, 255 to 0 and 127 to 128
			out[x][y] = c;//saves changes into a different array
		}
	}
	// and save this new image to file "outImage.pgm"
	writeImage(out, w, h);
}

```

```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 7 Task 2
  Description:
    The program reads a PGM image from the file "inImage.pgm" 
    and outputs a modified image to "outImage.pgm"
    Most code from task 0(code given),
    The code splits the image in half by outputing a picture with
    left half having its orginal color,and the right half having its color inverted.
*/
#include <iostream>
#include <cassert>
#include <cstdlib>
#include <fstream>
using namespace std;
	
const int MAX_W = 512;
const int MAX_H = 512;
// reads a PGM file.
// Notice that: width and height are passed by reference!
void readImage(int image[MAX_W][MAX_H], int &width, int &height) {
	char c;
	int x;
	ifstream instr;
	instr.open("inImage.pgm");
	// read the header P2
	instr >> c;
	assert(c == 'P');
	instr >> c;
	assert(c == '2');
	// skip the comments (if any)
	while ((instr>>ws).peek() == '#') {
		instr.ignore(4096, '\n');
	}
	instr >> width;
	instr >> height;
	assert(width <= MAX_W);
	assert(height <= MAX_H);
	int max;
	instr >> max;
	assert(max == 255);

	for (int row = 0; row < height; row++)
		for (int col = 0; col < width; col++)
			instr >> image[col][row];
	instr.close();
	return;
}

// Writes a PGM file

void writeImage(int image[MAX_W][MAX_H], int width, int height) {
	ofstream ostr;
	ostr.open("outImage.pgm");
	if (ostr.fail()) {
		cout << "Unable to write file\n";
		exit(1);
	};
	// print the header
	ostr << "P2" << endl;
	
	// width, height
	ostr << width << ' ';
	ostr << height << endl;
	ostr << 255 << endl;

	for (int row = 0; row < height; row++) {
		for (int col = 0; col < width; col++) {
			assert(image[col][row] < 256);
			assert(image[col][row] >= 0);
			ostr << image[col][row] << ' ';
			// lines should be no longer than 70 characters
			if ((col+1)%16 == 0) ostr << endl;
		}
		ostr << endl;
	}
	ostr.close();
	return;
}

int main() {
	int img[MAX_W][MAX_H];
	int w, h;
	readImage(img, w, h); // read it from the file "inImage.pgm"
	// w and h were passed by reference and now contain the dimensions of the picture
	// and the 2-dimesional array img contains the image data
	// Now we can manipulate the image the way we like
	// for example we copy its contents into a new array
	//white is 255, black is 0
	int out[MAX_W][MAX_H];
	for(int x = 0; x< w; x++) {
		for(int y = 0; y < h; y++) {
			int c = img[x][y];
			if(x<w/2){//everything on the left side at mid width point is normal
				out[x][y] = img[x][y];
			}
			else{//everything on the right side at mid width point is invered
				c = (c-255)*-1;//0 to 255, 255 to 0, 127 to 128
				out[x][y] = c;
			}
		}
	}
	// and save this new image to file "outImage.pgm"
	writeImage(out, w, h);
}
```
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 7 Task 3
  Description:
    The program reads a PGM image from the file "inImage.pgm",
    and outputs a modified image to "outImage.pgm"
    Most code from task 0(code given),
    Outputs a picture with a filled in white square at the center of the picture
*/

#include <iostream>
#include <cassert>
#include <cstdlib>
#include <fstream>
using namespace std;

const int MAX_W = 512;
const int MAX_H = 512;
// reads a PGM file.
// Notice that: width and height are passed by reference!
	
void readImage(int image[MAX_W][MAX_H], int &width, int &height) {
	char c;
	int x;
	ifstream instr;
	instr.open("inImage.pgm");
	// read the header P2
	instr >> c;
	assert(c == 'P');
	instr >> c;
	assert(c == '2');
	// skip the comments (if any)
	while ((instr>>ws).peek() == '#') {
		instr.ignore(4096, '\n');
	}
	instr >> width;
	instr >> height;
	assert(width <= MAX_W);
	assert(height <= MAX_H);
	int max;
	instr >> max;
	assert(max == 255);
	for (int row = 0; row < height; row++)
		for (int col = 0; col < width; col++)
			instr >> image[col][row];
	instr.close();
	return;
}

// Writes a PGM file
void writeImage(int image[MAX_W][MAX_H], int width, int height) {
	ofstream ostr;
	ostr.open("outImage.pgm");
	if (ostr.fail()) {
		cout << "Unable to write file\n";
		exit(1);
	};
	// print the header
	ostr << "P2" << endl;
	// width, height
	ostr << width << ' ';
	ostr << height << endl;
	ostr << 255 << endl;
	for (int row = 0; row < height; row++) {
		for (int col = 0; col < width; col++) {
			assert(image[col][row] < 256);
			assert(image[col][row] >= 0);
			ostr << image[col][row] << ' ';
			// lines should be no longer than 70 characters
			if ((col+1)%16 == 0) ostr << endl;
		}
		ostr << endl;
	}
	ostr.close();
	return;
}
	
int main() {
	int img[MAX_W][MAX_H];
	int w, h;
	readImage(img, w, h); // read it from the file "inImage.pgm"
	
	// w and h were passed by reference and now contain the dimensions of the picture
	// and the 2-dimesional array img contains the image data
	// Now we can manipulate the image the way we like
	// for example we copy its contents into a new array
	//white is 255, black is 0
	int out[MAX_W][MAX_H];
	for(int x = 0; x< w; x++) {
		for(int y = 0; y < h; y++) {
			int c = img[x][y];
			if(x<w/4 || x>w*3/4 || y<h/4 || y>h*3/4){
				out[x][y] = img[x][y];}
			else{
				c = 255;//129 = 126 and 255 = 0
				out[x][y] = c;}
		}
	}
	// and save this new image to file "outImage.pgm"
	writeImage(out, w, h);
}
```
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 7 Task 4
  Description:
    The program reads a PGM image from the file "inImage.pgm",
    and outputs a modified image to "outImage.pgm"
    Most code from task 0(code given),
    Outputs a picture with a thin white border square at the center of the picture
*/

#include <iostream>
#include <cassert>
#include <cstdlib>
#include <fstream>
using namespace std;

const int MAX_W = 512;
const int MAX_H = 512;

// reads a PGM file.
// Notice that: width and height are passed by reference!
void readImage(int image[MAX_W][MAX_H], int &width, int &height) {
	char c;
	int x;
	ifstream instr;
	instr.open("inImage.pgm");

	// read the header P2
	instr >> c;
	assert(c == 'P');
	instr >> c;
	assert(c == '2');

	// skip the comments (if any)
	while ((instr>>ws).peek() == '#') {
		instr.ignore(4096, '\n');

	}
	instr >> width;
	instr >> height;
	assert(width <= MAX_W);
	assert(height <= MAX_H);
	int max;
	instr >> max;
	assert(max == 255);
	
	for (int row = 0; row < height; row++)
		for (int col = 0; col < width; col++)
			instr >> image[col][row];
	instr.close();
	return;
}

// Writes a PGM file

void writeImage(int image[MAX_W][MAX_H], int width, int height) {
	ofstream ostr;
	ostr.open("outImage.pgm");
	if (ostr.fail()) {
		cout << "Unable to write file\n";
		exit(1);
	};

	// print the header
	ostr << "P2" << endl;
	// width, height
	ostr << width << ' ';
	ostr << height << endl;
	ostr << 255 << endl;

	for (int row = 0; row < height; row++) {
		for (int col = 0; col < width; col++) {
			assert(image[col][row] < 256);
			assert(image[col][row] >= 0);
			ostr << image[col][row] << ' ';
			// lines should be no longer than 70 characters
			if ((col+1)%16 == 0) ostr << endl;
		}
		ostr << endl;
	}
	ostr.close();
	return;
}

int main() {
	int img[MAX_W][MAX_H];
	int w, h;
	
	readImage(img, w, h); // read it from the file "inImage.pgm"
	
	// w and h were passed by reference and now contain the dimensions of the picture
	// and the 2-dimesional array img contains the image data
	// Now we can manipulate the image the way we like
	// for example we copy its contents into a new array
	//white is 255, black is 0
	int out[MAX_W][MAX_H];
	
	for(int x = 0; x< w; x++) {
		for(int y = 0; y < h; y++) {
			int c = img[x][y];
			// the == define the lines. The >= and <= limit the lines from overextending
			if((x==w/4 	&& y>=h/4 &&y<=h*3/4)	
			||(x==w*3/4 && y>=h/4 &&y<=h*3/4)	 
			||(y==h/4 	&& x>=w/4 &&x<=w*3/4)
			||(y==h*3/4	&& x>=w/4 &&x<=w*3/4)){
				out[x][y] = 255;}
			else{
				out[x][y] = img[x][y];
			}
		}
	}
	// and save this new image to file "outImage.pgm"
	writeImage(out, w, h);
}
```
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 7 Task 5
  Description:
    The program reads a PGM image from the file "inImage.pgm",
    and outputs a modified image to "outImage.pgm"
    Most code from task 0(code given),
    Outputs a picture twice the size of its original picture
*/

#include <iostream>
#include <cassert>
#include <cstdlib>
#include <fstream>
using namespace std;

const int MAX_W = 512;
const int MAX_H = 512;

// reads a PGM file.
// Notice that: width and height are passed by reference!

void readImage(int image[MAX_W][MAX_H], int &width, int &height) {
	char c;
	int x;
	ifstream instr;
	instr.open("inImage.pgm");

	// read the header P2
	instr >> c;
	assert(c == 'P');
	instr >> c;
	assert(c == '2');

	// skip the comments (if any)
	while ((instr>>ws).peek() == '#') {
		instr.ignore(4096, '\n');
	}
	instr >> width;
	instr >> height;

	assert(width <= MAX_W);
	assert(height <= MAX_H);
	int max;
	instr >> max;
	assert(max == 255);

	for (int row = 0; row < height; row++)
		for (int col = 0; col < width; col++)
			instr >> image[col][row];
	instr.close();
	return;
}

// Writes a PGM file
void writeImage(int image[MAX_W][MAX_H], int width, int height) {
	ofstream ostr;
	ostr.open("outImage.pgm");
	if (ostr.fail()) {
		cout << "Unable to write file\n";
		exit(1);
	};

	// print the header
	ostr << "P2" << endl;
	
	// width, height
	ostr << width << ' ';
	ostr << height << endl;
	ostr << 255 << endl;

	for (int row = 0; row < height; row++) {
		for (int col = 0; col < width; col++) {
			assert(image[col][row] < 256);
			assert(image[col][row] >= 0);
			ostr << image[col][row] << ' ';
			// lines should be no longer than 70 characters
			if ((col+1)%16 == 0) ostr << endl;
		}
		ostr << endl;
	}
	ostr.close();
	return;
}

int main() {
	int img[MAX_W][MAX_H];
	int w, h;
	readImage(img, w, h); // read it from the file "inImage.pgm"
	// w and h were passed by reference and now contain the dimensions of the picture
	// and the 2-dimesional array img contains the image data
	// Now we can manipulate the image the way we like
	// for example we copy its contents into a new array
	//white is 255, black is 0
	int out[MAX_W][MAX_H];
	for(int x = 0; x< w; x++) {
		for(int y = 0; y < h; y++) {
			out[2*x+0][2*y+0] = img[x][y];//the new array's placement is multiplied by 2
			out[2*x+0][2*y+1] = img[x][y];//inorder to prevent the color being saved
			out[2*x+1][2*y+0] = img[x][y];//in its original spot
			out[2*x+1][2*y+1] = img[x][y];//example (0 saves in 0,1)(1 saves in 2,3)(2 saves in 4,5)
		}
	}
	// and save this new image to file "outImage.pgm"
	writeImage(out, 2*w, 2*h);
}
	
```
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 7 Task 6
  Description:
    The program reads a PGM image from the file "inImage.pgm",
    and outputs a modified image to "outImage.pgm"
    Most code from task 0(code given),
    Outputs a picture that is pixelated by
    adveraging values in each "2x2 pixels" and giving each pixel in the "2x2 pixels" its adverage
*/

#include <iostream>
#include <cassert>
#include <cstdlib>
#include <fstream>
using namespace std;
	
const int MAX_W = 512;
const int MAX_H = 512;

// reads a PGM file.
// Notice that: width and height are passed by reference!
void readImage(int image[MAX_W][MAX_H], int &width, int &height) {
	char c;
	int x;
	ifstream instr;
	instr.open("inImage.pgm");

	// read the header P2
	instr >> c;
	assert(c == 'P');
	instr >> c;
	assert(c == '2');
	
	// skip the comments (if any)
	while ((instr>>ws).peek() == '#') {
		instr.ignore(4096, '\n');
	}
	instr >> width;
	instr >> height;
	assert(width <= MAX_W);
	assert(height <= MAX_H);
	int max;
	instr >> max;
	assert(max == 255);
	
	for (int row = 0; row < height; row++)
		for (int col = 0; col < width; col++)
			instr >> image[col][row];
	instr.close();
	return;
}
	
// Writes a PGM file
void writeImage(int image[MAX_W][MAX_H], int width, int height) {
	ofstream ostr;
	ostr.open("outImage.pgm");
	
	if (ostr.fail()) {
		cout << "Unable to write file\n";
		exit(1);
	};
	
	// print the header
	ostr << "P2" << endl;
	
	// width, height
	ostr << width << ' ';
	ostr << height << endl;
	ostr << 255 << endl;

	for (int row = 0; row < height; row++) {
		for (int col = 0; col < width; col++) {
			assert(image[col][row] < 256);
			assert(image[col][row] >= 0);
			ostr << image[col][row] << ' ';
			// lines should be no longer than 70 characters
			if ((col+1)%16 == 0) ostr << endl;
		}
		ostr << endl;
	}
	ostr.close();
	return;
}

int main() {
	int img[MAX_W][MAX_H];
	int w, h;
	
	readImage(img, w, h); // read it from the file "inImage.pgm"
	// w and h were passed by reference and now contain the dimensions of the picture
	// and the 2-dimesional array img contains the image data
	// Now we can manipulate the image the way we like
	// for example we copy its contents into a new array
	//white is 255, black is 0
	int out[MAX_W][MAX_H];
								//inorder to process 2x2 data
	for(int x = 0; x< w; x+=2) {//increment the for loop by 2
		for(int y = 0; y < h; y+=2) {//increment the for loop by 2
			int adv;
			adv = (img[x][y] + img[x+1][y] +img[x][y+1] +img[x+1][y+1])/4;
			out[x+0][y+0] = adv;//saving the adverage in 2x2 spaces
			out[x+0][y+1] = adv;
			out[x+1][y+0] = adv;
			out[x+1][y+1] = adv;
			}
		}
	// and save this new image to file "outImage.pgm"
	writeImage(out, w, h);
}
	
```
### Lab 8 
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 8 Task 1
  Description:
    The program reads a file and puts it into a structure (type Word) called w.
    Then it outputs the name of the country and its population at 2000.
*/
#include <iostream>
#include <fstream>
#include <cstdlib>

using namespace std;
const int MAXCOUNTRIES = 500;

struct Country{
	string name;
	int pop[8];
	};
	
struct World{
	int numcountries;
	Country countries[MAXCOUNTRIES];
	};
	
void readData(World &world);

int main(){						
	World w;
    readData(w);
    for(int i = 0; i<w.numcountries; i++)
   	{
    	cout<<w.countries[i].name<<" "<<w.countries[i].pop[6]<<endl;
   	}
}

void readData(World &world){

	ifstream f;
	f.open("population.csv");

	if (f.fail()){
		cout<<"Cannot find file"<<endl;
		exit(1);//cstdlib library
		}

	string nm;
	double p50,p70,p90,p10,p15;
	world.numcountries=0;

	while (f>>p50>>p70>>p90>>p10>>p15){
		getline(f,nm);
			Country c;
			c.name =nm;
			c.pop[0]= p50;
			c.pop[1]= (p50+p70)/2;
			c.pop[2]= p70;
			c.pop[3]= (p70+p90)/2;
			c.pop[4]= p90;
			c.pop[5]= (p90+p10)/2;
			c.pop[6]= p10;
			c.pop[7]= p15;
			
			world.countries[world.numcountries] = c;
			
			world.numcountries++;
	}
}

```
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 8 Task 2
  Description:
    The program reads a file nad puts it into a structure (type Word) called w.
    It calculates the countries relative growth rate and then
    outputs the maximum and minimum countries in terminal.
*/
#include <iostream>
#include <fstream>
#include <cstdlib>

using namespace std;
const int MAXCOUNTRIES = 500;

struct Country{
	string name;
	int pop[8];
	double relativeGrowth;
	};
	
struct World{
	int numcountries;
	Country countries[MAXCOUNTRIES];
	};
	
void readData(World &world, int &indexmin, int &indexmax);

int main(){						
	World w;
	int indexmin, indexmax;
    readData(w, indexmin, indexmax);
    cout<<"Maximum"<<w.countries[indexmax].name<<" "<<(w.countries[indexmax].relativeGrowth)*100<<"%"<<endl;
    cout<<"Minimum"<<w.countries[indexmin].name<<" "<<(w.countries[indexmin].relativeGrowth)*100<<"%"<<endl;

}

void readData(World &world, int &indexmin, int &indexmax){

	ifstream f;
	f.open("population.csv");

	if (f.fail()){
		cout<<"Cannot find file"<<endl;
		exit(1);//cstdlib library
		}

	string nm;
	double p50,p70,p90,p10,p15;
	world.numcountries=0;
	double min = 0;
	double max = 0;
	while (f>>p50>>p70>>p90>>p10>>p15){
		getline(f,nm);
		Country c;
		c.name =nm;
		c.pop[0]= p50;
		c.pop[1]= (p50+p70)/2;
		c.pop[2]= p70;
		c.pop[3]= (p70+p90)/2;
		c.pop[4]= p90;
		c.pop[5]= (p90+p10)/2;
		c.pop[6]= p10;
		c.pop[7]= p15;
		c.relativeGrowth=(p15 - p50) / p50;
			
		world.countries[world.numcountries] = c;

		if (world.countries[world.numcountries].relativeGrowth < min){
			min=world.countries[world.numcountries].relativeGrowth;
			indexmin=world.numcountries;
			}
		if (world.countries[world.numcountries].relativeGrowth > max){
			max=world.countries[world.numcountries].relativeGrowth;
			indexmax=world.numcountries;
			}
			
		world.numcountries++;
	}
}
```
```markdown
/*
  Author:Phillip Chen
  Course: 136
  Instructor: Alex Vikolaev
  Assignment: Lab 8 Task 3
  Description:
    The program reads a file nad puts it into a structure (type Word) called w.
   	It calculates the countries relative growth rate and then
   	places the countries with negative relative growth rate in a struct and prints it out 
*/
#include <iostream>
#include <fstream>
#include <cstdlib>

using namespace std;
const int MAXCOUNTRIES = 500;

struct Country{
	string name;
	int pop[8];
	double relativeGrowth;
	};
	
struct World{
	int numcountries;
	Country countries[MAXCOUNTRIES];
	};
	
void readData(World &world, int &indexmin, int &indexmax);

int main(){						
	World w;
	int indexmin, indexmax;
    readData(w, indexmin, indexmax);
	World negRG;
	int indexneg;
	
	for(int i =0; i < w.numcountries ; i++){
		if (w.countries[i].relativeGrowth<0){
		negRG.countries[indexneg]=w.countries[i];
		indexneg++;
		}
	}
	for(int i = 0; i < indexneg ; i++){
	cout<<negRG.countries[i].name
	<<'\t'<<negRG.countries[i].relativeGrowth
	<<'\t'<<negRG.countries[i].pop[7]
	<<endl;}
}

void readData(World &world, int &indexmin, int &indexmax){

	ifstream f;
	f.open("population.csv");

	if (f.fail()){
		cout<<"Cannot find file"<<endl;
		exit(1);//cstdlib library
		}

	string nm;
	double p50,p70,p90,p10,p15;
	world.numcountries=0;
	double min = 0;
	double max = 0;
	while (f>>p50>>p70>>p90>>p10>>p15){
		getline(f,nm);
		Country c;
		c.name =nm;
		c.pop[0]= p50;
		c.pop[1]= (p50+p70)/2;
		c.pop[2]= p70;
		c.pop[3]= (p70+p90)/2;
		c.pop[4]= p90;
		c.pop[5]= (p90+p10)/2;
		c.pop[6]= p10;
		c.pop[7]= p15;
		c.relativeGrowth=(p15 - p50) / p50;
			
		world.countries[world.numcountries] = c;

		if (world.countries[world.numcountries].relativeGrowth < min){
			min=world.countries[world.numcountries].relativeGrowth;
			indexmin=world.numcountries;
			}
		if (world.countries[world.numcountries].relativeGrowth > max){
			max=world.countries[world.numcountries].relativeGrowth;
			indexmax=world.numcountries;
			}
			
		world.numcountries++;
	}
}
```
### Lab 9
```markdown
/*
Author: Phillip Chen
Course: 136
Instructor: Alex Nikolaev
Assignment: Lab9a

This program will store an polynomial and computes its value.
First it will ask the highest degree in your polynomial ( x^degree ).
Second it will ask you to input constants next to each coefficent degree 
( Each "Number" in "Number x^degree" )  
Third it will ask you the value of the coefficent ( vaule of x )
Forth it will compute the vaule of the entire polynomial
*/
#include <iostream>
#include <cmath>
using namespace std;

void print(double poly[], int degree);
double eval(double poly[], int degree, double x);
double * readPolynomial(int &degree);

int main(){
	int degree;
	double *poly = readPolynomial(degree);
	print (poly, degree);
	
	int x;
	cout << "Input x: ";
	cin >> x;
	double result =	eval( poly, degree, x);
	cout << result << endl;
	delete[]poly;
	poly = NULL;
}

double * readPolynomial(int &degree){
	cout << "Enter the degree: ";
	cin >> degree;	
	double* d = new double[degree+1];
	for (int i = degree ; i>=0  ;i--){
		cout<<"Enter the coefficient at x^"<<i<<": ";
		cin>>d[i];
	}
	return d;
}
	

double eval(double poly[], int degree, double x){
	double result = 0.0;
	for (int i = degree ; i>=0  ;i--){
		result += poly[i]*pow(x,i);
		}
	return result;
} 

void print(double poly[], int degree){
	bool something_printed = false;
	for (int i = degree ; i>=0  ;i--){
		if (poly [i] != 0){
			if (something_printed == true){
				cout<<" + ";
				}
			if (i !=1 && i !=0){
				cout << poly[i] <<" x^"<<i;
				something_printed = true;
				}
			if (i == 1){
				cout << poly[i] <<" x ";
			}
			if (i == 0){cout << poly[i];}	
		}
		if (i == 0){
			cout << endl;
		}
	}
}
```
```markdown
/*
Author: Phillip Chen
Course: 136
Instructor: Alex Nikolaev
Assignment: Lab9 Task 2

This program will store an polynomial and computes its value.
First it will ask the highest degree in your polynomial ( x^degree ).
Second it will ask you to input constants next to each coefficent degree 
( Each "Number" in "Number x^degree" )  
Third it will ask you the value of the coefficent ( vaule of x )
Forth it will compute the vaule of the entire polynomial
*/
#include <iostream>
#include <cmath>
using namespace std;

void print(double poly[], int degree);
double eval(double poly[], int degree, double x);
double intersect(double poly1[], int degree1,double poly2[], int degree2 );
double * readPolynomial(int &degree);

int main(){
	int degree1;
	double *poly1 = readPolynomial(degree1);
	print (poly1, degree1);
	
	int degree2;
	double *poly2 = readPolynomial(degree2);
	print (poly2, degree2);
	
	double lowestx = intersect( poly1, degree1, poly2, degree2 );
	
	if (lowestx == 0.0){
		cout<<"There is no intersect"<<endl;
	}
	else{
		cout <<"There is an intersect: "<< lowestx << endl;
	}
	
	delete[]poly1;
	poly1 = NULL;
	delete[]poly2;
	poly2 = NULL;
}

double * readPolynomial(int &degree){
	cout << "Enter the degree: ";
	cin >> degree;	
	double* d = new double[degree+1];
	for (int i = degree ; i>=0  ;i--){
		cout<<"Enter the coefficient at x^"<<i<<": ";
		cin>>d[i];
	}
	return d;
}
	

double intersect(double poly1[], int degree1,double poly2[], int degree2){
	double result1 = 0.0;
	double result2 = 0.0;
	double x = 1;
	if (degree1 < degree2 && poly1[0] > poly2[0] ){ 
		while (result2>result1){				
			result1 = eval(poly1, degree1, x);
			result2 = eval(poly2, degree2, x);
				x += .1;
				cout<<x;
		}
	}
	if (degree1 > degree2 && poly1[0] < poly2[0] ){ 
		while (result2>result1){				
			result1 = eval(poly1, degree1, x);
			result2 = eval(poly2, degree2, x);
				x += .1;
				cout<<x;
		}
	}
	if (degree1 = degree2 && poly1[0] > poly2[0] ){ 
		while (result2>result1){				
			result1 = eval(poly1, degree1, x);
			result2 = eval(poly2, degree2, x);
				x += .1;
				cout<<x;
		}
	}
return x;
} 

double eval(double poly[], int degree, double x){
	double result = 0.0;
	for (int i = degree ; i>=0  ;i--){
		result += poly[i]*pow(x,i);
		}
	return result;
} 

void print(double poly[], int degree){
	bool something_printed = false;
	for (int i = degree ; i>=0  ;i--){
		if (poly [i] != 0){
			if (something_printed == true){
				cout<<" + ";
				}
			if (i !=1 && i !=0){
				cout << poly[i] <<" x^"<<i;
				something_printed = true;
				}
			if (i == 1){
				cout << poly[i] <<" x ";
			}
			if (i == 0){cout << poly[i];}	
		}
		if (i == 0){
			cout << endl;
		}
	}
}

```
### Lab 11
```markdown
/*
Author: Phillip Chen
Course: 136
Instructor: Alex Nikolaev
Assignment: Lab11 Task 1

This program makes an vector with 1,2,3,4,5,6,7,8,9,10 in it.
The function gets the sum of the values inside the vector by 
identifying the last element while removing that element from the vector. 
repeat that process until the vector is empty.
Once its empty, this is the base case (keeping the function from repeating infinitely) 
so we return a value (in this casue it is zero because we are doing addition and we dont want it
to affect the end result).
Then add all the number pulled out of the vector to get our answer
*/
#include <iostream>
#include <vector>
using namespace std;

int sum(vector<int> v); 
	
int main(){

	vector<int> v;
	for (int i = 1; i <=10; i++){
		v.push_back(i);
		}
	
	for (int i = 0; i <= v.size(); i++){
		cout<<v[i]<<" ";
		}cout<<endl;
		
	int result = sum(v); 
	cout<<result<<endl;
	return 0;
}

int sum(vector<int> v){
	if (v.size() > 0){
		int last = v[v.size()-1];
		v.pop_back();
		return sum(v) + last;
	}
	else
		return 0;	
}	
```
```markdown
/*
Author: Phillip Chen
Course: 136
Instructor: Alex Nikolaev
Assignment: Lab11 Task 2

This program makes an vector with random numbers in it.
The function gets maximum value in the vector by comparing the last two elements of the vector.
First I saved the last element of the vector on to a variable.
Then I compared that last element value with the 2nd last element of the vector.
Then I removed the last element in the vector and 
if the element removed was a bigger value, replace last spot in the vector.
if the element remove was a lower value, no change is needed.
Base case would be when the vector size is only 1 ( the maximum value in the vector ), returns itself.
*/
#include <iostream>
#include <vector>
#include <cstdlib>
using namespace std;

int maximum(vector<int> v); 
	
int main(){

	vector<int> v;
	for (int i = 1; i <=10; i++){
		v.push_back(rand() % 100 + 1);
		}
	for (int i = 0; i <= v.size()-1; i++){
		cout<<v[i]<<" ";
	}
	cout<<endl;
	int result = maximum(v);
	cout<<"Maximum:"<<result<<endl;
	return 0;
}

int maximum(vector<int> v){
	if (v.size() > 1){
		int last1 = v[v.size()-1];
		int last2 = v[v.size()-2];
		v.pop_back();

		if (last1 > last2){
			v[v.size()-1]=last1;
			return maximum(v);
		}
		else{
			return maximum(v);
		}
	}
	else
		return v[0];	
}
	
```
```markdown
/*
Author: Phillip Chen
Course: 136
Instructor: Alex Nikolaev
Assignment: Lab11 Task 3

This program takes a string input and decides if it is well-formed or not.
To be well formed the string has to have pairing symbols of [],{}, and <>.
For example <{[])> is well formed. <{{]}> is not well formed because {] is not the pairing correctly
*/
#include <iostream>
#include <string>
using namespace std;

bool wellFormed(string s); 

int main(){
	string s;
	cout<<"Please input string: ";
	getline(cin,s);
	
	bool result = wellFormed(s); 
	
	if (result == true){  
		cout<<"YES"<<endl;
	}
	else{
		cout<<"NO"<<endl;
	}
	return 0;
}

bool wellFormed(string s){
	if (s.size()>2){
		bool outer_symbols =( 	s[0]=='{' && s[s.size()-1]=='}' ||  
					s[0]=='[' && s[s.size()-1]==']'	||
					s[0]=='<' && s[s.size()-1]=='>');
		return ( outer_symbols && wellFormed(s.substr (1,s.size()-2) ) );
	}
	//base case when only 2 slot are left
	if (s.size()==2){
		bool outer_symbols =( 	s[0]=='{' && s[s.size()-1]=='}' ||  		
					s[0]=='[' && s[s.size()-1]==']' ||  		
					s[0]=='<' && s[s.size()-1]=='>');
		return ( outer_symbols );
	}
	//base case if the string 0th element isnt one of these symbol output true
	//if it is one of these symbol, then it is false because it does not have a symbol to pair with
	if (s.size()==1){
		return(s[0]!='{' && s[0]!='}'
		&& s[0]!='[' && s[0]!=']'
		&& s[0]!='<' && s[0]!='>');
	}
	if (s.size()==0){
		return true;
	}
}
```

