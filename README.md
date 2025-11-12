#include <iostream>
#include <vector>
#include <string>
using namespace std;

class User {
protected:
    string name, email, contact;
public:
    void setUser(string n, string e, string c) {
        name = n;
        email = e;
        contact = c;
    }
    void displayUser() {
        cout << "Name: " << name
             << "\nEmail: " << email
             << "\nContact: " << contact << endl;
    }
};

class Customer : public User {
    string address;
public:
    void setAddress(string a) {
        address = a;
    }
    void placeOrder() {
        cout << "Order placed successfully!\n";
    }
};

class FoodItem {
public:
    string itemName;
    float price;

    FoodItem(string n, float p) {
        itemName = n;
        price = p;
    }

    void displayItem() {
        cout << itemName << " - Rs." << price << endl;
    }
};

class Order {
    vector<FoodItem> items;
    float total = 0;
public:
    void addItem(FoodItem f) {
        items.push_back(f);
        total += f.price;
    }

    void showOrder() {
        cout << "\nOrder Details:\n";
        for (auto i : items)
            i.displayItem();
        cout << "Total Bill: Rs." << total << endl;
    }
};

int main() {
    Customer c;
    c.setUser("Sakshi", "sakshi@email.com", "9876543210");
    c.setAddress("Patna, Bihar");
    c.displayUser();
    c.placeOrder();

    FoodItem f1("Pizza", 250);
    FoodItem f2("Burger", 150);

    Order o;
    o.addItem(f1);
    o.addItem(f2);
    o.showOrder();

    return 0;
}

