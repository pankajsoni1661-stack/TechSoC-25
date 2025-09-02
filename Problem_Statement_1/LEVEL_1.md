#include <iostream>
#include <string>
#include <cctype>
using namespace std;

void Encode(string &Message, int Shift) {
    for (int i = 0; i < Message.length(); i++) {
        char m = Message[i];
        if (isalpha(m)) {
            char base = isupper(m) ? 'A' : 'a';
            Message[i] = (m - base + Shift + 26) % 26 + base;
        }
    }
}

void Decode(string &Message, int Shift) {
    for (int i = 0; i < Message.length(); i++) {
        char m = Message[i];
        if (isalpha(m)) {
            char base = isupper(m) ? 'A' : 'a';
            Message[i] = (m - base - Shift + 26) % 26 + base;
        }
    }
}

int main() {
    string Message;
    int Choice, Shift;

    cout << "\nEnter the Message : ";
    getline(cin, Message);

    cout << "\nEnter the Shift value : ";
    cin >> Shift;

    cout << "Choose an option:\n1. Encode\n2. Decode\nEnter Choice: ";
    cin >> Choice;

    if (Choice == 1) {
        Encode(Message, Shift);
        cout << "Encoded Message: " << Message << endl;
    } 
    else if (Choice == 2) {
        Decode(Message, Shift);
        cout << "Decoded Message: " << Message << endl;
    } 
    else {
        cout << "Invalid choice." << endl;
    }

    return 0;
}
