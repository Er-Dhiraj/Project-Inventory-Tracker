# Project-Inventory-Tracker
class Inventory:
    def __init__(self):
        self.items = {}

    def add_item(self, name, quantity, price):
        if name in self.items:
            print(f"{name} already exists. Use update_quantity to modify.")
        else:
            self.items[name] = {'quantity': quantity, 'price': price}
            print(f"Added {name} with quantity {quantity} and price {price}.")

    def update_quantity(self, name, quantity):
        if name in self.items:
            self.items[name]['quantity'] += quantity
            print(f"Updated {name}'s quantity to {self.items[name]['quantity']}.")
        else:
            print(f"{name} does not exist in inventory.")

    def update_price(self, name, price):
        if name in self.items:
            self.items[name]['price'] = price
            print(f"Updated {name}'s price to {price}.")
        else:
            print(f"{name} does not exist in inventory.")

    def delete_item(self, name):
        if name in self.items:
            del self.items[name]
            print(f"Deleted {name} from inventory.")
        else:
            print(f"{name} does not exist in inventory.")

    def view_inventory(self):
        if not self.items:
            print("Inventory is empty.")
        else:
            print("Current Inventory:")
            for name, details in self.items.items():
                print(f"{name}: Quantity = {details['quantity']}, Price = {details['price']}")

# Example Usage
if __name__ == "__main__":
    inventory = Inventory()

    while True:
        print("\nInventory Tracker")
        print("1. Add Item")
        print("2. Update Quantity")
        print("3. Update Price")
        print("4. Delete Item")
        print("5. View Inventory")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            name = input("Enter item name: ")
            quantity = int(input("Enter quantity: "))
            price = float(input("Enter price: "))
            inventory.add_item(name, quantity, price)
        elif choice == '2':
            name = input("Enter item name: ")
            quantity = int(input("Enter quantity to add/remove (use negative to reduce): "))
            inventory.update_quantity(name, quantity)
        elif choice == '3':
            name = input("Enter item name: ")
            price = float(input("Enter new price: "))
            inventory.update_price(name, price)
        elif choice == '4':
            name = input("Enter item name: ")
            inventory.delete_item(name)
        elif choice == '5':
            inventory.view_inventory()
        elif choice == '6':
            print("Exiting Inventory Tracker. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")
