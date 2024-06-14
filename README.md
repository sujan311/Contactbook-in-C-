# Contactbook-in-C-
Contactbook application code in C++ programming language
#include <iostream>
#include <string>
#include <map>

using namespace std;

class Phonebook {
private:
    map<string, string> phonebook;

public:
    void addEntry(string name, string number) {
        phonebook[name] = number;
    }

    void deleteEntry(string name) {
        phonebook.erase(name);
    }

    void searchEntry(string name) {
        if (phonebook.find(name)!= phonebook.end()) {
            cout << "Phone number of " << name << " is " << phonebook[name] << endl;
        } else {
            cout << "Entry not found" << endl;
        }
    }

    void displayPhonebook() {
        cout << "Phonebook entries:" << endl;
        for (auto it = phonebook.begin(); it!= phonebook.end(); ++it) {
            cout << it->first << ": " << it->second << endl;
        }
    }
};

int main() {
    Phonebook phonebook;

    int choice;
    string name, number;

    while (true) {
        cout << "Phonebook Application" << endl;
        cout << "1. Add entry" << endl;
        cout << "2. Delete entry" << endl;
        cout << "3. Search entry" << endl;
        cout << "4. Display phonebook" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter name: ";
                cin >> name;
                cout << "Enter phone number: ";
                cin >> number;
                phonebook.addEntry(name, number);
                break;
            case 2:
                cout << "Enter name to delete: ";
                cin >> name;
                phonebook.deleteEntry(name);
                break;
            case 3:
                cout << "Enter name to search: ";
                cin >> name;
                phonebook.searchEntry(name);
                break;
            case 4:
                phonebook.displayPhonebook();
                break;
            case 5:
                return 0;
            default:
                cout << "Invalid choice" << endl;
        }
    }

    return 0;
}
