# **Food Ordering App – SRS + Wireframe Design (POC)**

---

# **1. Introduction**

## **1.1 Purpose**

This document defines the Software Requirements Specification (SRS) and wireframe layout for a Food Ordering Subscription-Based Mobile Application. The app allows users to register using Name, Email, Phone Number, auto-location fetch, OTP verification (WhatsApp + Email), login using OTP, browse predefined meal packages, select a subscription, customize date range, choose delivery location, and complete payment.

## **1.2 Scope**

The app includes:

* User Registration & Login with OTP
* Auto location fetch
* Meal package listing with filters
* Meal details view
* Subscription booking with date range and exclusions
* Payment integration
* Basic user dashboard/home

---

# **2. System Requirements**

## **2.1 Functional Requirements**

### **FR-01: User Registration**

* User enters **Name, Email, Phone**.
* App fetches **current GPS location** in background.
* On submit, backend generates a **6-digit OTP**.
* OTP is sent to **Email & WhatsApp (same OTP)**.
* User enters OTP to verify.

### **FR-02: User Login**

* Login using **Phone Number + OTP**.
* OTP is sent to Email and WhatsApp.

### **FR-03: Home Screen**

* Display:

  * User name
  * Current location
* Meal package sections:

  * **3-time meal**
  * **2-time meal**
  * **1-time meal**
* Filter:

  * **Veg / Non-Veg**

### **FR-04: Meal Details Screen**

* Show meal name
* Items included
* Description
* Per-day rate
* Button: **Book Meal**

### **FR-05: Booking Flow**

* User selects **date range**.
* User can **remove specific dates**.
* App calculates:

  * Number of days
  * Total price = (days × per-day rate)
* User selects delivery location from **predefined location list**.
* Proceed to **payment gateway**.

### **FR-06: Payment**

* Integration with Razorpay/Stripe.

---

## **2.2 Non-Functional Requirements**

* App must load within 3 seconds.
* OTP delivery within 10 seconds.
* Payment must be secure (SSL enabled).
* Should support Android + iOS.

---

# **3. System Architecture Overview**

* **Frontend:** React Native
* **Backend:** Firebase / Node.js / Supabase (POC flexible)
* **Database:** Firebase Firestore / Realtime DB
* **Auth:** Custom OTP via Cloud Functions
* **Notification API:** WhatsApp (Twilio / Meta Cloud API) + Email
* **Payment:** Razorpay

---

# **4. Wireframes**

Below are ASCII wireframes for POC-level UI.

---

# **4.1 Registration Screen**

```
 -------------------------------------
|            Register                 |
 -------------------------------------
| Name:       [____________________]  |
| Email:      [____________________]  |
| Phone:      [____________________]  |
| (Auto fetch location internally)    |
|                                      |
|         [ Register ]                 |
 -------------------------------------
```

---

# **4.2 OTP Verification Screen**

```
 -------------------------------------
|          OTP Verification           |
 -------------------------------------
| Enter OTP: [ _ _ _ _ _ _ ]          |
|                                      |
|        [ Verify OTP ]               |
|        [ Resend OTP ]               |
 -------------------------------------
```

---

# **4.3 Login Screen**

```
 -------------------------------------
|              Login                  |
 -------------------------------------
| Phone Number: [__________________]  |
|                                      |
|          [ Send OTP ]               |
 -------------------------------------
```

---

# **4.4 Home Screen**

```
 -------------------------------------------------
|  Hi, Vivek                                      |
|  Location: Bangalore, India                     |
 -------------------------------------------------
|  Filter: [Veg] [Non-Veg]                        |
 -------------------------------------------------
|  3-Time Meal                                    |
|   - Package A  [View Details]                   |
|   - Package B                                    |
 -------------------------------------------------
|  2-Time Meal                                    |
|   - Package C                                    |
 -------------------------------------------------
|  1-Time Meal                                    |
|   - Package D                                    |
 -------------------------------------------------
```

---

# **4.5 Meal Details Screen**

```
 -------------------------------------------------
|  Meal Name: Premium 3-Time Meal                |
|                                                 |
|  Breakfast Items:                              |
|   - Idli, Dosa, Upma                           |
|                                                 |
|  Lunch Items:                                   |
|   - Rice, Curry, Dal, Veg Fry                   |
|                                                 |
|  Dinner Items:                                  |
|   - Chapati, Veg Sabzi, Salad                   |
|                                                 |
|  Rate per Day: ₹150                             |
|                                                 |
|               [ Book Now ]                      |
 -------------------------------------------------
```

---

|  Meal Name: Premium 3-Time Meal                |
|  Items: Chapati, Rice, Curry, Veg, Salad        |
|  Rate per Day: ₹150                             |
|                                                 |
|               [ Book Now ]                      |
---------------------------------------------------

```

---

# **4.6 Booking Flow (Date Range + Remove Dates)**
```

---

## |              Choose Date Range                     |

| From: [ dd-mm-yyyy ]   To: [ dd-mm-yyyy ]          |
|                                                     |
| Remove Dates:                                       |
|  [ ] 05 Jan   [ ] 10 Jan   [ ] 15 Jan              |
|  (User selects dates to exclude)                    |
-------------------------------------------------------

| Days Selected: 22                                   |
| Per Day Rate: ₹150                                  |
| Total Amount: ₹3300                                 |
|                                                     |
|        [ Choose Delivery Location ]                 |
-------------------------------------------------------

```

---

# **4.7 Choose Predefined Location**
```

---

## |            Select Delivery Location                |

|  ( ) MG Road                                        |
|  ( ) Silk Board                                     |
|  ( ) Koramangala                                   |
|  ( ) Whitefield                                    |
------------------------------------------------------

## |                  [ Proceed to Pay ]                 |

```

---

# **4.8 Payment Screen**
```

---

## |                  Payment                           |

|  Amount: ₹3300                                     |
|  Payment via Razorpay                              |
|                                                    |
|               [ Pay Now ]                          |
------------------------------------------------------

```

---

# **5. Data Model (High-Level)**

## **Users**
```

userId
name
email
phone
location { lat, lng, address }
verified: true/false
createdAt

```

## **Meal Packages**
```

packageId
name
type: 3-meal / 2-meal / 1-meal
vegType: veg / non-veg
items[]
ratePerDay

```

## **Bookings**
```

bookingId
userId
packageId
dateRange { start, end }
removedDates[]
totalDays
totalAmount
deliveryLocation
paymentStatus

```

---

# **6. POC Deliverables**
- Working Registration + Login with OTP
- Meal list screens
- Meal details
- Booking flow
- Payment gateway integration
- Firebase/Backend functions for OTP + booking logic

---

# **End of Document**

```
