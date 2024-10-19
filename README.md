# CODESOFT5
class Contact:
    def __init__(self, name, phone, email, address):
        self.name = name
        self.phone = phone
        self.email = email
        self.address = address

class ContactBook:
    def __init__(self):
        self.contacts = []

    def add_contact(self):
        name = input("Enter name: ")
        phone = input("Enter phone number: ")
        email = input("Enter email: ")
        address = input("Enter address: ")
        self.contacts.append(Contact(name, phone, email, address))
        print("Contact added successfully!")

    def view_contacts(self):
        if not self.contacts:
            print("No contacts available.")
        else:
            print("Contact List:")
            for index, contact in enumerate(self.contacts, start=1):
                print(f"{index}. {contact.name} - {contact.phone}")

    def search_contact(self):
        query = input("Enter name or phone number to search: ")
        found = False
        for contact in self.contacts:
            if contact.name.lower() == query.lower() or contact.phone == query:
                print(f"Name: {contact.name}")
                print(f"Phone: {contact.phone}")
                print(f"Email: {contact.email}")
                print(f"Address: {contact.address}")
                found = True
                break
        if not found:
            print("Contact not found.")

    def update_contact(self):
        self.view_contacts()
        index = int(input("Enter contact number to update: ")) - 1
        if index >= 0 and index < len(self.contacts):
            contact = self.contacts[index]
            print("Enter new details (press Enter to skip):")
            contact.name = input(f"Name ({contact.name}): ") or contact.name
            contact.phone = input(f"Phone ({contact.phone}): ") or contact.phone
            contact.email = input(f"Email ({contact.email}): ") or contact.email
            contact.address = input(f"Address ({contact.address}): ") or contact.address
            print("Contact updated successfully!")
        else:
            print("Invalid contact number.")

    def delete_contact(self):
        self.view_contacts()
        index = int(input("Enter contact number to delete: ")) - 1
        if index >= 0 and index < len(self.contacts):
            del self.contacts[index]
            print("Contact deleted successfully!")
        else:
            print("Invalid contact number.")

def main():
    contact_book = ContactBook()
    while True:
        print("\nContact Management System")
        print("----------------------------")
        print("1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Quit")
        choice = input("Enter your choice: ")
        if choice == "1":
            contact_book.add_contact()
        elif choice == "2":
            contact_book.view_contacts()
        elif choice == "3":
            contact_book.search_contact()
        elif choice == "4":
            contact_book.update_contact()
        elif choice == "5":
            contact_book.delete_contact()
        elif choice == "6":
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
