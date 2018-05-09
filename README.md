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
### Jekyll Themes


### Support or Contact
