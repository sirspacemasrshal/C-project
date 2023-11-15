#include <iostream>
#include <string>
#include <set>
#include <iomanip>
using namespace std;

class Hotel {
private:
    struct Node {
        int id, customerID;
        string name, roomtype, date;
        bool isDeleted;
        int checkoutDate;
        Node* next;
    };
    Node* head = nullptr;
    Node* deletedHead = nullptr;

public:
    void menu();
    void insert();
    void search();
    void update();
    void deleteRoom();
    void show();
    void showDeletedRooms();
};

void Hotel::menu() {
    int choice;
    cout << "\n";
    cout << "\tWelcome To Hotel Management System Application\n" << endl;
    cout << "\n\t_____Hotel Management System_____";
    cout << "\n\nS.No     Functions                         Description" << endl;
    cout << "\n1\tAllocate Room\t\t\tInsert New Room";
    cout << "\n2\tSearch Room\t\t\tSearch Room with RoomID or CustomerID";
    cout << "\n3\tUpdate Room\t\t\tUpdate Room Record";
    cout << "\n4\tDelete Room\t\t\tDelete Room with RoomID";
    cout << "\n5\tShow Room Records\t\t\tShow Room Records that (we Added)";
    cout << "\n6\tShow Deleted Rooms\t\t\tShow Deleted Room Records";
    cout << "\n7\tExit" << endl;

    cout << "Enter Choice: ";
    cin >> choice;

    switch (choice) {
        case 1:
            insert();
            menu();
            break;

        case 2:
            search();
            menu();
            break;

        case 3:
            update();
            menu();
            break;

        case 4:
            deleteRoom();
            menu();
            break;

        case 5:
            show();
            menu();
            break;

        case 6:
            showDeletedRooms();
            menu();
            break;

        case 7:
            cout << "Exiting the application." << endl;
            break;

        default:
            cout << "Invalid choice" << endl;
            menu();
            break;
    }
}

void Hotel::insert() {
    cout << "\n\t_____Hotel Management System_____"<<endl;
    
    // Create a set to keep track of allocated room IDs
    set<int> allocatedRoomIDs;
    
    Node* ptr = head;
    while (ptr != nullptr) {
        allocatedRoomIDs.insert(ptr->id);
        ptr = ptr->next;
    }
    
    cout << "Available Room IDs: "<<endl;
    for (int i = 1; i <= 99; i++) {
        
        if (allocatedRoomIDs.find(i) == allocatedRoomIDs.end()) {
            cout << setw(2) << setfill('0') << i << " ";
        }
        if(i % 10 == 0){
            cout << endl;
        }
    }
    
    int newRoomID;
    cout << "\nEnter Room ID: ";
    cin >> newRoomID;

    // Check if the entered room ID is valid
    if (newRoomID < 1 || newRoomID > 100) {
        cout << "Invalid room ID. Please enter a valid room ID between 1 and 100." << endl;
        return;
    }

    // Check if a room with the same ID already exists
    ptr = head;
    while (ptr != nullptr) {
        if (newRoomID == ptr->id) {
            cout << "Room with the same ID already exists." << endl;
            return;
        }
        ptr = ptr->next;
    }

    Node* new_node = new Node;
    new_node->id = newRoomID;

    cout << "\nEnter Customer Name: ";
    cin.ignore();
    getline(cin, new_node->name);

    cout << "\nEnter Customer ID: ";
    cin >> new_node->customerID;

    cout << "\nAllocated Date: ";
    cin >> new_node->date;

    cout << "\nEnter Room Type (single/double/twin): ";
    cin.ignore();
    getline(cin, new_node->roomtype);

    new_node->isDeleted = false;
    new_node->checkoutDate = 0; // Initialize checkout date to 0

    new_node->next = nullptr;

    if (head == nullptr) {
        head = new_node;
    } else {
        ptr = head;
        while (ptr->next != nullptr) {
            ptr = ptr->next;
        }
        ptr->next = new_node;
    }
    cout << "\n\n\t\t New Room Inserted" << endl;
}

void Hotel::search() {
    cout << "\n\t_____Hotel Management System_____";
    int searchChoice;
    cout << "\nChoose Search Option:" << endl;
    cout << "1. Search by Room ID" << endl;
    cout << "2. Search by Customer ID" << endl;
    cout << "Enter your choice: ";
    cin >> searchChoice;

    if (searchChoice == 1) {
        int t_id;
        if (head == nullptr) {
            cout << "\n\nLinked list is Empty" << endl;
        } else {
            cout << "\nEnter Room ID: ";
            cin >> t_id;
            Node* ptr = head;
            bool found = false;

            while (ptr != nullptr) {
                if (!ptr->isDeleted && t_id == ptr->id) {
                    found = true;
                    cout << "\nRoom ID: " << ptr->id << endl;
                    cout << "Customer Name: " << ptr->name << endl;
                    cout << "Customer ID: " << ptr->customerID << endl;
                    cout << "Room Allocated Date: " << ptr->date << endl;
                    cout << "Room Type: " << ptr->roomtype << endl;
                    cout << "Status: Active" << endl;
                    cout << "Checkout Date: " << (ptr->checkoutDate > 0 ? to_string(ptr->checkoutDate) : "None") << endl;
                    break;
                }
                ptr = ptr->next;
            }

            if (!found) {
                cout << "Room not found." << endl;
            }
        }
    } else if (searchChoice == 2) {
        int t_customerID;
        if (head == nullptr) {
            cout << "\n\nLinked list is Empty" << endl;
        } else {
            cout << "\nEnter Customer ID: ";
            cin >> t_customerID;
            Node* ptr = head;
            bool found = false;

            while (ptr != nullptr) {
                if (!ptr->isDeleted && t_customerID == ptr->customerID) {
                    found = true;
                    cout << "\nRoom ID: " << ptr->id << endl;
                    cout << "Customer Name: " << ptr->name << endl;
                    cout << "Customer ID: " << ptr->customerID << endl;
                    cout << "Room Allocated Date: " << ptr->date << endl;
                    cout << "Room Type: " << ptr->roomtype << endl;
                    cout << "Status: Active" << endl;
                    cout << "Checkout Date: " << (ptr->checkoutDate > 0 ? to_string(ptr->checkoutDate) : "None") << endl;
                }
                ptr = ptr->next;
            }

            if (!found) {
                cout << "Customer not found." << endl;
            }
        }
    } else {
        cout << "Invalid choice." << endl;
    }
}

void Hotel::update() {
    cout << "\n\t_____Hotel Management System_____";
    int t_id;
    if (head == nullptr) {
        cout << "\n\nLinked list is Empty" << endl;
    } else {
        cout << "\nEnter Room ID: ";
        cin >> t_id;
        Node* ptr = head;

        while (ptr != nullptr) {
            if (!ptr->isDeleted && t_id == ptr->id) {
                cout << "\n\nRoom ID: ";
                cin >> ptr->id;

                cout << "\n\nCustomer Name: ";
                cin.ignore();
                getline(cin, ptr->name);

                cout << "\n\nCustomer ID: ";
                cin >> ptr->customerID;

                cout << "\n\nAllocated Date: ";
                cin >> ptr->date;

                cout << "\n\nRoom Type: ";
                cin.ignore();
                getline(cin, ptr->roomtype);

                cout << "\n\n\t\t Update Record Successfully" << endl;
                return;
            }
            ptr = ptr->next;
        }

        cout << "Room not found." << endl;
    }
}

void Hotel::deleteRoom() {
    cout << "\n\t_____Hotel Management System_____";
    int t_id;
    if (head == nullptr) {
        cout << "\n\nLinked list is Empty" << endl;
    } else {
        cout << "\nEnter Room ID: ";
        cin >> t_id;

        Node* pre = nullptr;
        Node* ptr = head;

        while (ptr != nullptr) {
            if (!ptr->isDeleted && t_id == ptr->id) {
                if (pre == nullptr) {
                    head = ptr->next;
                } else {
                    pre->next = ptr->next;
                }

                ptr->isDeleted = true;

                cout << "Enter Checkout Date (e.g., 20231031 for October 31, 2023): ";
                cin >> ptr->checkoutDate;

                // Add the deleted room to the deleted room list
                ptr->next = deletedHead;
                deletedHead = ptr;

                cout << "Delete Room Record Successfully" << endl;
                return;
            }
            pre = ptr;
            ptr = ptr->next;
        }
        cout << "Room not found." << endl;
    }
}

void Hotel::show() {
    Node* ptr = head;
    cout << "\n\t_____Hotel Management System_____";
    cout << "\nActive Room Records:\n";

    while (ptr != nullptr) {
        if (!ptr->isDeleted) {
            cout << "\nRoom ID: " << ptr->id << endl;
            cout << "Customer Name: " << ptr->name << endl;
            cout << "Customer ID: " << ptr->customerID << endl;
            cout << "Room Allocated Date: " << ptr->date << endl;
            cout << "Room Type: " << ptr->roomtype << endl;
            cout << "Status: Active" << endl;
            cout << "Checkout Date: " << (ptr->checkoutDate > 0 ? to_string(ptr->checkoutDate) : "None") << endl;
        }
        ptr = ptr->next;
    }
}

void Hotel::showDeletedRooms() {
    Node* ptr = deletedHead;
    cout << "\n\t_____Hotel Management System_____";
    cout << "\nDeleted Room Records:\n";

    while (ptr != nullptr) {
        cout << "\nRoom ID: " << ptr->id << endl;
        cout << "Customer Name: " << ptr->name << endl;
        cout << "Customer ID: " << ptr->customerID << endl;
        cout << "Room Allocated Date: " << ptr->date << endl;
        cout << "Room Type: " << ptr->roomtype << endl;
        cout << "Status: Deleted" << endl;
        cout << "Checkout Date: " << (ptr->checkoutDate > 0 ? to_string(ptr->checkoutDate) : "None") << endl;

        ptr = ptr->next;
    }
}

int main() {
    Hotel h;
    h.menu();
    return 0;
}
