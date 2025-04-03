//Pitsa_yetkazish_xizmati
#include <iostream> 
#include <vector> 
#include <string> 
using namespace std;

struct Pizza { 
string name; 
double price;
};

struct Order { 
string customer; 
vector<Pizza> pizzas; 
string status; 
};

vector<Pizza> menu = {
{"Margherita", 5.99}, {"Pepperoni", 7.49}, {"BBQ Chicken", 8.99}, {"Veggie", 6.99} };

vector<Order> orders;

void showMenu() { 
cout << "\nPIZZA MENU:" << endl;
for (size_t i = 0;
i < menu.size(); 
i++) { 
cout << i + 1 << ". " << menu[i].name << " - $" << menu[i].price << endl;
} 
}

void placeOrder() { 
Order newOrder; 
cout << "\nEnter your name: ";
cin >> newOrder.customer;

int choice;
while (true) {
    showMenu();
    cout << "Choose a pizza (0 to finish): ";
    cin >> choice;
    if (choice == 0) break;
    if (choice > 0 && choice <= menu.size()) {
        newOrder.pizzas.push_back(menu[choice - 1]);
    } else {
        cout << "Invalid choice! Try again." << endl;
    }
}

newOrder.status = "Preparing";
orders.push_back(newOrder);
cout << "\nOrder placed successfully!" << endl;

}

void showOrders() { 
cout << "\nCURRENT ORDERS:" << endl;
for (size_t i = 0;
i < orders.size();
i++) { 
cout << i + 1 << ". " << orders[i].customer << " - Status: " << orders[i].status << endl;
} 
}

int main() { 
int option;
while (true) { 
cout << "\n1. Show Menu\n2. Place Order\n3. Show Orders\n4. Exit\nChoose an option: ";
cin >> option;
switch (option) { 
case 1: showMenu();break; 
case 2: placeOrder();break; 
case 3: showOrders(); break; 
case 4: return 0; default: cout << "Invalid option! Try again." << endl; } } }


