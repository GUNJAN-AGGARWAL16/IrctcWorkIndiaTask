# WorkIndiaIRCTC
=======

# IRCTC (Railway Management System API) 

The IRCTC (Railway Management System API) is designed where users can come on the platform and check if there are any trains available between 2 stations.
The app will also display how many seats are available between any 2 stations and the user can book a seat if the availability > 0 after logging in. Since this has to be real-time and multiple users can book seats simultaneously,so the code must be optimized enough to handle large traffic and should not fail while doing any bookings.
If more than 1 users simultaneously try to book seats, only either one of the users should be able to book. Handle such race conditions while booking.
There is a Role Based Access provision and 2 types of users would exist :
1. Admin - can perform all operations like adding trains, updating total seats in a train, etc.
2. Login users - can check availability of trains, seat availability, book seats, get booking details, etc.

## Features

1. Register a User
Create an endpoint for registering a user.
2. Login User
Provide the ability to the user to log into his account
3. Add a New Train
An endpoint for the admin to create a new train with a source and destination
4. Get Seat Availability
Create an endpoint for the users where they can enter the source and destination and fetch all the trains between that route with their availabilities
5. Book a Seat
Create an endpoint for the users to book a seat on a particular train
6. Get Specific Booking Details
Create an endpoint for the users to book a seat on a particular train

## Getting Started

1.Web Server: Node.js

2.PostgreSQL

### Prerequisites

- Node.js
- npm (Node Package Manager)
- Supabase account and project setup

### Setting Up the Environment

1. Clone the repository to your local machine:

   ```
   git clone 
   ```

2. Install the necessary npm packages:

   ```
   cd scalable-reservation-system
   npm install
   ```

3. Set up your Supabase project and obtain the Supabase URL and Key. Update the `.env` file with your Supabase credentials and other environment variables:

   ```
   PORT=port
   ADMIN_API_KEY=random_string
   SUPABASE_URL=your_supabase_url
   SUPABASE_KEY=your_supabase_key
   JWT_SECRET=your_jwt_secret
   ```

### Running the API

Start the server with:

```
npm start
```

The API will be available at `http://localhost:{PORT}`.

## API Endpoints

### Users

- **POST /api/users/register**: Register a new user.
    - for registering a admin include the `ADMIN_API_KEY` in query params as `apiKey`
- **POST /api/users/login**: Log in a user.

` All the Train and Booking endpoints are protected, set the Authorization header = Bearer {Token sent while login} for accessing these endpoints.`

### Trains

- **POST /api/trains/add** (Admin only): Add a new train.
- **GET /api/trains/availability**: Check seat availability between two stations.

### Bookings

- **POST /api/bookings/book**: Book a seat on a train.
- **GET /api/bookings/details**: Get specific booking details.
- **GET /api/bookings/userBookings**: Get booking history of a user.


