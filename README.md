# ZenBoost App

This project implements a simple web application for ZenBoost, featuring a user quiz and a basic checkout page with a dynamic discount based on estimated purchasing power.

## Demo

You can check out the live demo hosted on Vercel - https://zenboost-frontend.vercel.app/

## Links
* Frontend Repository: [Link to Frontend Repository on GitHub](https://github.com/RuSh991/zenboost-frontend)
* Backend Repository: [Link to Backend Repository on GitHub](https://github.com/RuSh991/zenboost-backend)


## Features

1. **User Quiz**

   - Age range (18-25, 26-35, 36-45, 46+)
   - Gender (Male, Female, Other/Prefer not to say)
   - Reason for purchase (Work productivity, Sports performance, Study aid, General energy boost)
   - Zip code (5-digit US zip code)

2. **Checkout Page**

   - Display a simple product (ZenBoost, $29 for a pack of 12)
   - Show a personalized discount based on estimated purchasing power
   - Include fields for name, email, and payment methods

3. **Discount Calculation / Estimated Purchasing Power**

    **Loading ZIP Code Income Data**

    The server loads income data from a JSON file (income_by_zip.json) located in the same directory as the server file.


    Estimating a user's purchasing power based on their:
	1.	ZIP Code: Represents local economic conditions using income data.
	2.	Age Range: Assumes different age groups have different purchasing powers.
	3.	Device Type: Desktop users are given higher purchasing power than mobile users.
	4.	Device Value: The value of the device they use, normalized by a maximum assumed value of $3000.

    First, the function determines income for the provided zip code from a dataset. It normalizes this income on a scale of 0-1, comparing it with the highest and lowest incomes in the dataset. Next, the function calculates a purchasing power "age factor," where it is assumed that older age groups have higher purchasing power and younger age groups have lesser. It assigns a higher factor to desktop users compared to other device types and normalizes the device value (maximum value assumed is $3000).

    The final purchasing power estimate is a weighted sum of these factors: 40% from zip code income, 30% from age, 20% from device type, and 10% from device value.

    The getAgeFactor function provides the purchasing power multiplier based on the provided age range.

    1. Age 18-25 corresponds to a factor of 0.3 (lower purchasing power),
    2. Age 26-35 corresponds to 0.5 (moderate purchasing power),
    3. Age 36-45 corresponds to 0.8 (higher purchasing power),
    4. Age 46+ corresponds to 1 (highest purchasing power).
    If an invalid age range is provided apart from the above ones, the function defaults to a value of 0.4.

    **Discount Calculation**

    There is an inverse relationship between purchasing power and discount. Higher purchasing power would correspond to a lower discount and vice versa. Discount ranges from 5% (highest purchasing power) to 30% (lowest purchasing power).


4. **Responsive Design**

## Technical Requirements

- Frontend Framework: React.js
- Backend: NodeJS

## Getting Started

### Prerequisites

- Node.js installed on your local machine
- Git installed on your local machine

### Installation

1. Clone both the repositories from Github:

2. Start the frontend and backend by following the steps in each of the repositories - [Backend](https://github.com/RuSh991/zenboost-backend) and [Frontend](https://github.com/RuSh991/zenboost-frontend)


## Hosting

The ZenBoost app is hosted on two different platforms for the frontend and backend services:

- **Frontend Hosting**: The frontend is hosted on [Vercel](https://vercel.com)
- **Backend Hosting**: The backend is hosted on [Render](https://render.com), backend URL - https://zenboost-backend.onrender.com
