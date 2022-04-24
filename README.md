# Machine Coding - Parking Lot

## Problem Statement
A parking lot is an area where cars can be parked for a certain amount of time. A parking lot can have multiple floors with each floor having a different number of slots and each slot being suitable for different types of vehicles.<br>
For this problem, we have to design the next generation parking lot system which can manage a parking lot without any human intervention.

## Requirements
Create a command-line application for the parking lot system with the following requirements.

The functions that the parking lot system can do:
- Create the parking lot.
- Add floors to the parking lot.
- Add a parking lot slot to any of the floors.
- Given a vehicle, it finds the first available slot, books it, creates a ticket, parks the vehicle, and finally returns the ticket.
- Unparks a vehicle given the ticket id.
- Displays the number of free slots per floor for a specific vehicle type.
- Displays all the free slots per floor for a specific vehicle type.
- Displays all the occupied slots per floor for a specific vehicle type.
- Details about the Vehicles: <br>
Every vehicle will have a type, registration number, and color.
- Different Types of Vehicles: <br>
  1\. Car <br>
  2\. Bike <br>
  3\. Truck <br>
- Details about the Parking Slots: <br>
  1\. Each type of slot can park a specific type of vehicle. <br>
  2\. No other vehicle should be allowed by the system. <br>
  3\. Finding the first available slot should be based on: <br>
     &nbsp;&nbsp;&nbsp;
     a\. The slot should be of the same type as the vehicle. <br>
     &nbsp;&nbsp;&nbsp; 
     b\. The slot should be on the lowest possible floor in the parking lot. <br>
     &nbsp;&nbsp;&nbsp;
     c\. The slot should have the lowest possible slot number on the floor. <br>
     &nbsp;&nbsp;&nbsp;
     d\. Numbered serially from 1 to n for each floor where n is the number of parking slots on that floor. <br>
- Details about the Parking Lot Floors: <br>
  1\. Numbered serially from 1 to n where n is the number of floors. <br>
  2\. Might contain one or more parking lot slots of different types. <br>
  3\. We will assume that the first slot on each floor will be for a truck, the next 2 for bikes, and all the other slots for cars. <br>
- Details about the Tickets: <br>
The ticket id would be of the following format: <br>
<parking_lot_id>_<floor_no>_<slot_no> <br>
Example: PR1234_2_5 (denotes 5th slot of 2nd floor of parking lot PR1234) <br>
We can assume that there will only be 1 parking lot. The ID of that parking lot is PR1234.

## Input/Output Format
The code should strictly follow the input/output format and will be tested with provided test cases.

### Input Format
Multiple lines with each line containing a command.

Possible commands:

- `create_parking_lot <parking_lot_id> <no_of_floors> <no_of_slots_per_floor>`
- `park_vehicle <vehicle_type> <reg_no> <color>`
- `unpark_vehicle <ticket_id>`
- `display <display_type> <vehicle_type>` <br>
Possible values of display_type: `free_count`, `free_slots`, `occupied_slots`
- `exit`

Stop taking the input when you encounter the word `exit`.

### Output Format
Print output based on the specific commands as mentioned below.

- `create_parking_lot` <br>
Created parking lot with <no_of_floors> floors and <no_of_slots_per_floor> slots per floor

- `park_vehicle` <br>
Parked vehicle. Ticket ID: <ticket_id> <br>
Print "Parking Lot Full" if slot is not available for that vehicle type.

- `unpark_vehicle` <br>
Unparked vehicle with Registration Number: <reg_no> and Color: <color> <br>
Print "Invalid Ticket" if ticket is invalid or parking slot is not occupied.

- `display free_count <vehicle_type>` <br>
No. of free slots for <vehicle_type> on Floor <floor_no>: <no_of_free_slots> <br>
The above will be printed for each floor.

- `display free_slots <vehicle_type>` <br>
Free slots for <vehicle_type> on Floor <floor_no>: <comma_separated_values_of_slot_nos> <br>
The above will be printed for each floor.

- `display occupied_slots <vehicle_type>` <br>
Occupied slots for <vehicle_type> on Floor <floor_no>: <comma_separated_values_of_slot_nos> <br>
The above will be printed for each floor.

## Example
```
create_parking_lot PR1234 2 6
Created parking lot with 2 floors and 6 slots per floor

display free_count CAR
No. of free slots for CAR on Floor 1: 3
No. of free slots for CAR on Floor 2: 3

display free_count BIKE
No. of free slots for BIKE on Floor 1: 2
No. of free slots for BIKE on Floor 2: 2

display free_slots BIKE
Free slots for BIKE on Floor 1: 2,3
Free slots for BIKE on Floor 2: 2,3

display free_slots TRUCK
Free slots for TRUCK on Floor 1: 1
Free slots for TRUCK on Floor 2: 1

display occupied_slots CAR
Occupied slots for CAR on Floor 1: 

park_vehicle CAR KA-01-DB-1234 black
Parked vehicle. Ticket ID: PR1234_1_4

display occupied_slots CAR
Occupied slots for CAR on Floor 1: 4
Occupied slots for CAR on Floor 2: 

unpark_vehicle PR1234_1_4
Unparked vehicle with Registration Number: KA-01-DB-1234 and Color: black

park_vehicle TRUCK KA-32-SJ-5389 orange
Parked vehicle. Ticket ID: PR1234_1_1

park_vehicle TRUCK KL-54-DN-4582 green
Parked vehicle. Ticket ID: PR1234_2_1

park_vehicle TRUCK KL-12-HF-4542 green
Parking Lot Full

exit
```