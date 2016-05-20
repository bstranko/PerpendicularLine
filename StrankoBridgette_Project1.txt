#include <iostream>
using namespace std;

int main()
{
//Declaring the variables where the (x and y) coordinates for P are (a,b) Q are (c, d) and f are (e,f)
//The slope and y intercept for PQ is m_one, b_one, 
//The slope and y intercept for R is m_two, b_two,
//The x and y coordinates are x_coordinate, y_coordinate
 	double a, b, c, d, e, f;
	double m_one, b_one, m_two, b_two, x_coordinate, y_coordinate;
	
//Informing the user of the purpose of this program
	cout<<"This program: \n" <<endl
		<<"\t *Asks that you provide the coordinates for points \"P\", \"Q\". \"R\" " << endl
		<<"\t  where input data is precise to tenths \n" << endl
		<<"\t *Finds the slope and y intercept of the line" << endl
		<<"\t  which passing through points \"P\" and \"Q\" \n" << endl 
		<<"\t *Finds the slope and y intercept of the line which is " << endl
		<<"\t  perpendicular to the line through \"P\" and \"Q\" " << endl
		<<"\t  and which passes through a third point \"R\" \n" << endl 
		<<"\t *Then provides the point of intersection of these two lines \n" << endl; 

//Informing the user how to enter the data into the program
	cout<<"Don't forget: only enter one digit pass the decimal!\n" 
	    <<"Enter a space between the coordinate values then press enter \n" << endl

//requesting the values for the points PQR from the user
		<<"Please provide the (x,y) coordinates of the point P: \t";
	cin>> a>> b; 
		
	cout <<"Please provide the (x,y) coordinates of the point Q: \t";
	cin>> c>>d;

	cout <<"Please provide the (x,y) coordinates of the point R: \t";
	cin>> e>>f;

//Setting the precision of the decimal to tenths as mentioned in the instructions above	
	cout.setf(ios::fixed);
	cout.setf(ios::showpoint);
	cout.precision(1);

//Putting out the points to the screen P: (a,b)  Q: (c,d)  R: (e,f) 
	cout <<"\nP: " <<" (" <<a  <<" , " << b << ") Q: " <<" (" <<c <<" , " <<d<< ") R" << " (" <<e<< " , " <<f<< ")" 
    <<endl
	<<endl;

/* The formula that will be used to find the slopes, y intercepts and points of intersection is

			m_one = (d-b) / (c-a);
			b_one = (b*c-d*a) / (c-a);
			m_two =-(c-a) / (d-b);
			b_two= (f*d-f*b + c*e-a*e) / (d-b);
			x_coordinate = (b_one - b_two) / (m_two - m_one);
			y_coordinate = m_one*(( b_one - b_two)/( m_two - m_one)) + b_one; 

Before using the formula, the progam is eliminating some of the possible points that could break the formula*/

	if ((a==c) && (b==d)) 
	{
		cout <<"The points P & Q are the same and no solution can be provided!\n"
			 <<"Two different points are needed to form a line!" << endl;
	}

//There is a lot of division in this formula, and the program wants to avoid division by zero
//The next few statements should avoid division by zero 

// (m_one - m_two)  is part of a denominator and division by zero is not possible.  
//To see if (m_two – m_one) = 0 we need to first make sure that neither c-a or d-b = 0 
//because they are in the denominators of the slopes.  
//Then we need to calculate ((d-b) / (c-a)) +(c-a) / (d-b))  !0.   
//Since I cannot think of a scenario when this might happen, the output to the screen will be something //silly, just in case there is a scenario that I am missing.	

else if ((c-a!= 0) && (d-b != 0) &&  (((d-b) / (c-a)) +(c-a) / (d-b)) == 0)
{
    		cout<<"Division by zero is impossible! You sunk my battleship!";

}

else if ((c-a == 0) && (c!= 0)) 
		
		{
		    cout.precision(2);
	    	    
                  cout <<"For the line which passing through points \"P\" and \"Q\"" << endl 
			  <<"\t The slope is undefined" <<endl
			  <<"\t There is no y intercept" << endl
			  << endl

			  <<"For the line which is perpendicular to the line through \"P\" and \"Q\" " << endl
			  <<"and which passes through a third point \"R\" \n" 
			  <<"\t The slope is: 0.00" <<endl
			  <<"\t The y intercept is: " <<f <<endl
			  << endl
			  <<"The point of intersection for these two lines is: " 
			  <<"(" << a << " , " << f << ")" 
			  << endl;

		}

	else if (c-a == 0) 
		
		{
		    cout.precision(2);

		    cout <<"For the line which passing through points \"P\" and \"Q\"" << endl 
			  <<"\t The slope is undefined" <<endl
			  <<"\t PQ is a vertical line on the y axis. \n"
			  <<"The y intercept is any real number!" 
              << endl
			  << endl

			  <<"For the line which is perpendicular to the line through \"P\" and \"Q\" " << endl
			  <<"and which passes through a third point \"R\" \n" 
			  <<"\t The slope is: 0.00" <<endl
			  <<"\t The y intercept is: " <<f <<endl
			  << endl

			  <<"The point of intersection for these two lines is: " 
			  <<"(" << a << " , " << f << ")" 
			  << endl;
		}


	else if ((d-b == 0) && (e!=0)) 
		{
		    cout.precision(2);
  		    cout <<"For the line which passing through points \"P\" and \"Q\"" << endl 
			  <<"\t The slope is: 0.00" <<endl
			  <<"\t The y intercept is: " <<b <<endl
			  << endl

			  <<"For the line which is perpendicular to the line through \"P\" and \"Q\" " << endl
			  <<"and which passes through a third point \"R\" \n" 
			  <<"\t The slope is undefined" <<endl
			  <<"\t There is no y intercept" << endl
			  << endl

			  <<"The point of intersection for these two lines is: " 
			  <<"(" << e << " , " << b << ")" 
			  << endl;
		}
	
	else if (d-b == 0) 
		{
			cout.precision(2);

			cout <<"For the line which passing through points \"P\" and \"Q\"" << endl 
				 <<"\t The slope is: 0.00" <<endl
				 <<"\t The y intercept is: " <<b <<endl
				 << endl

				 <<"For the line which is perpendicular to the line through \"P\" and \"Q\" " 
                              << endl
				 <<"and which passes through a third point \"R\" \n" 
				 <<"\t The slope is undefined" <<endl
				 <<"\t The line that passes through R is a vertical line on the y axis." <<endl
				 <<"\t The y intercept is any real number!" << endl
				  << endl

				 <<"The point of intersection for these two lines is: " 
				 <<"(" << e << " , " << b << ")" 
				 << endl;
	
	}

//This system will now try to find the slopes, y intercept and point of intersection using the formula 
	else
		{

			m_one = (d-b) / (c-a);
			b_one = (b*c-d*a) / (c-a);
			m_two =-1*(c-a) / (d-b);
			b_two= (f*d-f*b + c*e-a*e) / (d-b);
			x_coordinate = (b_one - b_two) / (m_two - m_one);
			y_coordinate = m_one*(( b_one - b_two)/( m_two - m_one)) + b_one;

			cout.precision(2);
			cout <<"For the line which passing through points \"P\" and \"Q\"" << endl 
				 <<"\t The slope is: " <<m_one <<endl
				 <<"\t The y intercept is: " <<b_one <<endl
			        << endl

				 <<"For the line which is perpendicular to the line through \"P\" and \"Q\" " 
 << endl
				 <<"and which passes through a third point \"R\" \n" 
				 <<"\t The slope is: " <<m_two <<endl
				 <<"\t The y intercept is: " <<b_two <<endl
				 << endl

		         	 <<"The point of intersection for these two lines is: " 
				 <<"(" << x_coordinate << " , " << y_coordinate << ")" 
				 << endl;
		 }
	
			return 0;
}
