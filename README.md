# Bus Reservation System

**C++ · Object-Oriented Programming · Console UI**

A menu-driven academic C++ application modeling bus registration and seat reservations.

## Engineering highlights

- Add buses, driver details, route and departure information.
- Reserve seats and display a 32-seat layout (8 rows × 4 seats).
- View registered buses and reservation information.

## Project files

| File | Purpose |
| --- | --- |
| [Bus Reservation System.cpp](Bus%20Reservation%20System.cpp) | Original C++ source |

## How to explore or reproduce

Use a Windows-compatible C++ compiler or IDE supporting `conio.h`. With MinGW, an example build command is `g++ "Bus Reservation System.cpp" -o bus_reservation.exe`. Run the resulting executable with synthetic passenger information only.

## Suggested test cases

- Register a bus and verify its route and departure information.
- Check first, last and every fourth seat boundary, plus invalid seat numbers.
- Attempt a duplicate reservation and verify the displayed availability.
- Register more than the supported capacity and check bounds handling.

These are proposed tests, not passing test results.

## Scope and limitations

The original implementation has fixed-size character arrays, unchecked bus capacity, invalid seat indexing for multiples of four, and a shared counter that is modified during seat display. These need correction before reliable use. No build or runtime testing was performed in this documentation update.

## Portfolio

[Hassan Ali Janjua — Engineering portfolio](https://github.com/HassanAliJanjua03)
