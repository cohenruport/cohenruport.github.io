---
layout: project
type: project
image: img/Hotel.png
title: "Hotel Management System"
date: 2023-12
published: true
labels:
  - C++
summary: "My team developed a hotel management system using C++ for our ICS 212 final"
---

For this project we were tasked with creating a hotel management system in C++ which tracks all of the rooms and customers in a hotel. We used a switch case to provide the user with a menu. The menu offers the user 7 options such as checking what rooms are available, checking in customers, searching for customers and various other functions. Additionally the _Manage Room_ function opens another menu which allows the user to create new rooms in the hotel, find rooms, or delete existing rooms.

My team and I developed the structure of our solution collectively and worked individually on the different menu functions. I worked to develop the check in room function and  Manage Room function which presents another menu using a switch case and shows other functions I created; add room and delete room.

Here is code for my function check in room which checks to see if the room number entered is available and then takes the customer information and marks the room as unavailable.

```
void hotelManagement::checkInRoom() 
{
    int rNum;
    divider(); //just a divider to make code print cleaner
    //get number of room we want to check in 
    cout << "Enter room number" << endl; 
    cin >> rNum;

    // loop through rooms to check if room is available
    for (int i = 0; i < rooms.size(); i++)
    {
        Room &r = rooms[i];
        if (rNum == r.getRoomNum())
        {
            if (false == r.isAvailable())
            {
                cout << "Error: Room is already in use" << endl;
                return; // note: we end here if room is unavailable
            }
            else
            {
                cout << "Room is available" << endl;
                Customer c;
                this->customers.push_back(c); //to take customer information 
                cout << "Customer checked-in successfully..." << endl;
                rooms[i].setAvailable(false); //mark that the room is occupied
                return;
            }
        }
    }
    // if we get here, we didn't find the room number which means there is noi room in the system with that number
    cout << "Error: Room not found" << endl;
}
```
