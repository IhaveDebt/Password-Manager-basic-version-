#include <iostream>
#include <map>
#include <string>
using namespace std;

int main() {
    map<string, string> passwordVault; // store service → password
    int choice;

    while (true) {
        cout << "\n=== Simple Password Manager ===\n";
        cout << "1. Add a new password\n";
        cout << "2. Retrieve a password\n";
        cout << "3. Show all services stored\n";
        cout << "4. Exit\n";
        cout << "Choose an option: ";
        cin >> choice;

        if (choice == 1) {
            string service, password;
            cout << "Enter service name: ";
            cin >> service;
            cout << "Enter password: ";
            cin >> password;
            passwordVault[service] = password;
            cout << "Password saved!\n";
        }
        else if (choice == 2) {
            string service;
            cout << "Enter service name: ";
            cin >> service;
            if (passwordVault.find(service) != passwordVault.end()) {
                cout << "Password for " << service << ": " << passwordVault[service] << endl;
            } else {
                cout << "No password stored for " << service << ".\n";
            }
        }
        else if (choice == 3) {
            cout << "Stored services:\n";
            for (auto &entry : passwordVault) {
                cout << "- " << entry.first << endl;
            }
        }
        else if (choice == 4) {
            cout << "Exiting... Stay safe!\n";
            break;
        }
        else {
            cout << "Invalid option, try again.\n";
        }
    }

    return 0;
}
