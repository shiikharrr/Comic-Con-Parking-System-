Comic-Con Parking System ER Diagram
Overview

This ER diagram represents a multi-zone parking management system designed for a large event such as Comic-Con. The system tracks vehicles entering the venue, assigns parking spots based on type and availability, manages parking sessions, and records payments.

The design supports different vehicle types, reserved parking categories, reusable parking spots, and multiple visits by the same vehicle.

Workflow

The system follows this sequence:

Vehicle → Ticket → Parking Session → Parking Spot → Payment

A vehicle enters the facility and receives a ticket. A parking session is created with entry time and assigned spot. When the vehicle exits, the session is updated with exit time and payment is recorded.

Entities
Vehicle

Stores information about vehicles entering the parking facility.
Attributes:
vehicle_id (PK), vehicle_number, vehicle_category_id (FK), owner_name

Vehicle_Category

Defines types of vehicles.
Attributes:
category_id (PK), name

Parking_Zone

Represents different zones or levels in the parking facility.
Attributes:
zone_id (PK), name, level

Parking_Spot

Represents individual parking slots.
Attributes:
spot_id (PK), zone_id (FK), spot_category_id (FK), spot_number, is_active

Spot_Category

Defines reserved categories of parking spots.
Attributes:
spot_category_id (PK), name

Ticket

Represents entry record issued to a vehicle.
Attributes:
ticket_id (PK), vehicle_id (FK), issued_at, status

Parking_Session

Tracks entry and exit of a vehicle.
Attributes:
session_id (PK), vehicle_id (FK), spot_id (FK), ticket_id (FK), entry_time, exit_time, status

Payment

Stores payment details for a parking session.
Attributes:
payment_id (PK), session_id (FK), amount, payment_time, status, method

Relationships

One vehicle category can have many vehicles.

One vehicle can have many tickets.
One vehicle can have many parking sessions over time.

One parking zone can have many parking spots.
One spot category can have many parking spots.

One parking spot can be used in many parking sessions over time.

One ticket is associated with one parking session.

One parking session belongs to one vehicle and one parking spot.

One parking session can have one or more payments.

Design Decisions

Parking sessions are the core entity and track entry and exit times, allowing the system to determine which vehicles are currently inside.

Parking spots are reusable across multiple sessions, which reflects real world usage.

Spot categories allow modeling of reserved parking such as VIP, staff, exhibitors, and EV charging.

Vehicle categories ensure that appropriate parking spots can be assigned based on vehicle type.

Tickets are separated from parking sessions to distinguish entry records from full parking lifecycle tracking.

Payments are linked to parking sessions to support flexible billing and real world scenarios.

Assumptions

A vehicle can enter the parking facility multiple times during the event.

A parking spot can be reused by different vehicles across different sessions.

Each parking session corresponds to one ticket.

Payments are made after the parking session is completed.

Er diagram 

<img width="1478" height="773" alt="er diagram " src="https://github.com/user-attachments/assets/9d8e4eec-5652-4add-87a7-8f2a5205d8fe" />


Conclusion

This ER diagram models a scalable and practical parking system for a large event. It supports multiple zones, reserved parking, session tracking, and payment handling while maintaining clean structure and proper normalization.



Author 
Shikhar Gupta
