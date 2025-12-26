# Task-3
contacts = []

def display_menu():
    print("\nContact Book Menu:")
    print("1. Add New Contact")
    print("2. View All Contacts")
    print("3. Search by Name")
    print("4. Delete Contact")
    print("5. Exit")

def add_contact():
    name = input("Enter name: ")
    phone = input("Enter phone number: ")
    email = input("Enter email: ")
    contact = {"name": name, "phone": phone, "email": email}
    contacts.append(contact)
    print(f"Contact '{name}' added successfully!")

def view_contacts():
    if not contacts:
        print("No contacts available.")
    else:
        print("\nAll Contacts:")
        for i, contact in enumerate(contacts, 1):
            print(f"{i}. Name: {contact['name']}, Phone: {contact['phone']}, Email: {contact['email']}")

def search_contact():
    name = input("Enter name to search: ")
    found_contacts = [c for c in contacts if c['name'].lower() == name.lower()]
    if found_contacts:
        for contact in found_contacts:
            print(f"Name: {contact['name']}, Phone: {contact['phone']}, Email: {contact['email']}")
    else:
        print("Contact not found.")

def delete_contact():
    name = input("Enter name to delete: ")
    global contacts
    contacts = [c for c in contacts if c['name'].lower() != name.lower()]
    print(f"Contact '{name}' deleted (if existed).")

def main():
    while True:
        display_menu()
        choice = input("Enter your choice: ")
        if choice == '1':
            add_contact()
        elif choice == '2':
            view_contacts()
        elif choice == '3':
            search_contact()
        elif choice == '4':
            delete_contact()
        elif choice == '5':
            print("Exiting contact book.")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()