








#include <iostream>
#include <iomanip>
#include <vector>
using namespace std;

// Room for rent

int main()
{
    string name;
    char confirmChoice;
    char continueChoice;

    cout << "Enter your name: ";
    cin >> name;
    cout << "Hi, " << name << "! Welcome to the Room for Rent." << endl;

    // Validating alphabet only
    for (char c : name) {
        if (!isalpha(c)) {
            cout << "Error: Only alphabets are allowed in the name." << endl;
            return 1; // Error
        }
    }

    vector<bool> roomAvailability(10, true); // Vector to track room availability

    do {
        // Room selection
        int chosenRoom;
        cout << "Choose a room (1-10): ";
        cin >> chosenRoom;

        // Validate the room number
        if (cin.fail() || chosenRoom < 1 || chosenRoom > 10) {
            cout << "Error: Please choose a room between 1 and 10 only." << endl;
            return 1; // Error
        }

        // Check the room availability
        if (!roomAvailability[chosenRoom - 1]) {
            cout << "Error: Room " << chosenRoom << " is already taken. Please choose another room." << endl;
            continue;
        }

        // Switch statement
        int rent;
        int squareMeter;
        switch (chosenRoom) {
            case 1:
                rent = 4000;
                squareMeter = 20;
                break;
            case 2:
                rent = 4500;
                squareMeter = 25;
                break;
            case 3:
                rent = 5000;
                squareMeter = 30;
                break;
            case 4:
                rent = 5500;
                squareMeter = 35;
                break;
            case 5:
                rent = 6000;
                squareMeter = 40;
                break;
            case 6:
                rent = 6500;
                squareMeter = 45;
                break;
            case 7:
                rent = 7000;
                squareMeter = 50;
                break;
            case 8:
                rent = 7500;
                squareMeter = 55;
                break;
            case 9:
                rent = 8000;
                squareMeter = 60;
                break;
            case 10:
                rent = 8500;
                squareMeter = 65;
                break;
            default:
                cout << "Unexpected error in room selection switch statement." << endl;
                return 1; // Error
        }

        // Display room details
        cout << "Room Details for Room " << chosenRoom << ":" << endl;
        cout << "Location : 666 Kalye Imperno street napico manggahan manila city " << endl;  
        cout << "Own Cr, Sink" << endl;
        cout << "Fully tiles" << endl;
        cout << "Aircon slot" << endl; 
        cout << "Near Schools (U-Belt)" << endl; 
        cout << "Near Choice Market" << endl; 
        cout << "good for 2 persons with minimal appliances" << endl;
        cout << "Square Meter: " << setw(11) << squareMeter << " sqm" << endl;
        cout << "Rent: " << setw(20) << "₱" << rent << " per month" << endl;
        cout << "Water Billing: " << setw(23) << "₱180 per head" << endl;
        cout << "Electric Billing: " << setw(20) << "₱350 per head" << endl;

        // Calculate total payment
        int waterBilling = 180;
        int electricBilling = 350;
        int totalPayment = rent + waterBilling + electricBilling;

        cout << "Total Payment: " << setw(11) << "₱" << totalPayment << endl;
        cout << "Only cash payments can be accepted." << endl;


        // Payment confirmation
        cout << "Do you want to rent this room? (Y/N): ";
        cin >> confirmChoice;

        // Update status of room
        cout << "Updating the status of room " << chosenRoom;
        if (confirmChoice == 'Y' || confirmChoice == 'y') {
            cout << " as unavailable." << endl;
            roomAvailability[chosenRoom - 1] = false; // Mark the room as unavailable
        } else {
            cout << " as available." << endl;
        }

        // Ask if the user wants to continue
        cout << "Do you want to choose another room? (Y/N): ";
        cin >> continueChoice;

    } while (continueChoice == 'Y' || continueChoice == 'y');

    // Exit after the transaction
    cout << "Exit. Have a nice day! " << endl;

    return 0;
}
