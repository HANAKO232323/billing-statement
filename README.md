#include <iostream>
#include <vector>
#include <string>
#include <iomanip> // For formatting output

using namespace std;

struct Household {
    string name;
    double water_usage;
    double bill_amount;
};

// Vector to store household data
vector<Household> households;

// Function to add a household
void addHousehold() {
    Household h;
    cout << "\nEnter household name: ";
    cin.ignore(); // Ignore previous newline
    getline(cin, h.name);
    cout << "Enter water usage (cubic meters): ";
    cin >> h.water_usage;
    
    // Calculate bill (PHP 20 per cubic meter)
    h.bill_amount = h.water_usage * 20; 

    households.push_back(h);
    cout << "\n✅ Household added successfully!\n";
}

// Function to view household records
void viewHouseholds() {
    if (households.empty()) {
        cout << "\n⚠️ No household records available.\n";
        return;
    }
    
    cout << "\n🏠 Household Records:\n";
    cout << setw(20) << left << "Name" << setw(15) << "Water Usage" << "Bill (PHP)\n";
    cout << "-----------------------------------------\n";

    for (const auto &h : households) {
        cout << setw(20) << left << h.name 
             << setw(15) << h.water_usage 
             << fixed << setprecision(2) << h.bill_amount << endl;
    }
}

// Main menu function
void menu() {
    int choice;
    do {
        cout << "\n🚰 Barangay Water Billing System";
        cout << "\n1️⃣  Add Household";
        cout << "\n2️⃣  View Households";
        cout << "\n3️⃣  Exit";
        cout << "\nEnter choice: ";
        cin >> choice;
        
        switch (choice) {
            case 1:
                addHousehold();
                break;
            case 2:
                viewHouseholds();
                break;
            case 3:
                cout << "\n👋 Exiting program...\n";
                break;
            default:
                cout << "\n❌ Invalid choice, please try again!\n";
        }
    } while (choice != 3);
}

// Main function
int main() {
    menu();
    return 0;
}
