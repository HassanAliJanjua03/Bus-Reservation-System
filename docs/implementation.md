# Implementation notes

This project explores bus registration and seat booking through a menu-driven C++ console program. The [original source](../Bus%20Reservation%20System.cpp) is preserved.

## Data model

The original class is named `a`. Its private members contain fixed-size character arrays for bus number, driver, arrival and departure times, route and the `bus_seat[8][4][10]` matrix. The program declares five bus objects in `bus[5]`. These are array capacities, not guarantees that the code safely enforces them.

## Reservation design

For seat number s, after validating 1 <= s <= 32, the intended zero-based row is (s-1)/4 and the column is (s-1)%4. The original uses s/4 and (s%4)-1, which makes the column negative for seats divisible by four and the row out of range at seat 32.

## Known issues and future improvements

| Observed issue | Improvement |
| --- | --- |
| Global `t` tracks both registered buses and empty seats | Use distinct counters or derive values from containers |
| Some search loops use y <= t | Restrict searches to registered objects |
| Bus insertion has no array capacity check | Validate capacity or use a vector |
| Seat indexing does not validate lower bounds and is incorrect at row boundaries | Validate range and use the corrected mapping |
| Fixed character buffers read via extraction without length checks | Use std::string and validate input |
| Input failure and invalid menu choices lack robust handling | Recover or terminate cleanly |
| In-memory records only | Add file persistence if needed |
| Windows-specific console header and command | Use portable console I/O |

Because of these issues, the original code may access memory outside its arrays. Do not rely on it for actual reservations or enter real passenger data.

## Suggested validation plan

| Scenario | Expected behavior after correction |
| --- | --- |
| Add one valid bus | Fleet displays one bus, all 32 seats empty |
| Book seats 1, 4, 5 and 32 | Correct row and column for every seat |
| Book the same seat twice | Reject second booking |
| Enter seat 0, negative number or 33 | Reject before indexing |
| Search an unknown bus | Inform the user without reading unregistered objects |
| Display reservations then browse fleet | Fleet count remains unchanged |
| Add a sixth bus | Reject or grow the collection safely |
| Restart the program | In-memory bookings are cleared |

These are proposed checks, not completed tests. The original source has not been compiled or run for this documentation update. The corrected mapping shown in the README is an improvement idea, not a change to the original source.

[Back to project](../README.md)
