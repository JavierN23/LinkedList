Create LinkedList in C++, Adding and Deleting Nodes.


    #include <iostream>
    using namespace std;

    struct Node {
    int data;  //Stores Value
    Node* next; //Pointer
    
    Node(int value) : data(value), next(nullptr) {}
    
    };


    class LinkedList {
    public:

    Node* head; 
    
    LinkedList() : head(nullptr) {}
    
    void addNodeAtStart(int value) {
        Node* newNode = new Node(value);
        newNode->next = head;
        head = newNode; 
        
    }

    void deleteNodeAtStart() {
        if (head == nullptr) {
            cout << "List is empty. Cannot delete." << endl;
            return;
        }
        Node* temp = head; 
        head = head->next;  
        delete temp;  
    }

    void displayList() {
        if (head == nullptr) {
            cout << "List is empty." << endl;
            return;
        }
        Node* temp = head;
        while (temp != nullptr) {
            cout << temp->data << " -> ";
            temp = temp->next;
        }
        cout << "nullptr" << endl;
    }

    ~LinkedList() {
        while (head != nullptr) {
            deleteNodeAtStart();
        }
    }
      };

      int main() {
    LinkedList list;

    list.addNodeAtStart(1);
    list.addNodeAtStart(2);
    list.addNodeAtStart(3);

    cout << "List after adding nodes at the start:" << endl;
    list.displayList();

    list.deleteNodeAtStart();
    cout << "List after deleting the node at the start:" << endl;
    list.displayList();  
    
    list.deleteNodeAtStart();
    cout << "List after deleting another node at the start:" << endl;
    list.displayList();  
    
    list.deleteNodeAtStart();
    cout << "List after deleting the last node at the start:" << endl;
    list.displayList(); 

    return 0;
    }
