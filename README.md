# python-practical-tasks

#TASK BASED ON COMPUTER HEADWARE (BACKEND)

pc_parts = {
    "CPU": [
        {"name": "Intel Core i9-13900K", "price": 599.99, "stock": 10},
        {"name": "AMD Ryzen 9 7950X", "price": 549.99, "stock": 8},
    ],
    "GPU": [
        {"name": "NVIDIA RTX 4090", "price": 1599.99, "stock": 5},
        {"name": "AMD Radeon RX 7900 XTX", "price": 999.99, "stock": 6},
    ],
    "Motherboard": [
        {"name": "ASUS ROG STRIX Z790-E", "price": 399.99, "stock": 12},
        {"name": "MSI MAG B650 TOMAHAWK", "price": 259.99, "stock": 15},
    ],
    "RAM": [
        {"name": "Corsair Vengeance DDR5 32GB", "price": 149.99, "stock": 20},
        {"name": "G.SKILL Trident Z5 RGB 32GB", "price": 169.99, "stock": 18},
    ],
    "Storage": [
        {"name": "Samsung 980 PRO 2TB SSD", "price": 179.99, "stock": 25},
        {"name": "Western Digital Black 4TB HDD", "price": 129.99, "stock": 30},
    ],
    "Power Supply": [
        {"name": "Corsair RM850x 850W", "price": 129.99, "stock": 10},
        {"name": "EVGA SuperNOVA 750W", "price": 119.99, "stock": 12},
    ],
    "Case": [
        {"name": "NZXT H510 Elite", "price": 149.99, "stock": 8},
        {"name": "Lian Li PC-O11 Dynamic", "price": 169.99, "stock": 10},
    ],
    "Cooling": [
        {"name": "Noctua NH-D15", "price": 99.99, "stock": 15},
        {"name": "Corsair iCUE H150i Elite", "price": 159.99, "stock": 12},
    ],
    "Peripherals": [
        {"name": "Logitech G502 HERO Mouse", "price": 49.99, "stock": 25},
        {"name": "Razer BlackWidow Keyboard", "price": 129.99, "stock": 20},
    ],
    "Monitor": [
        {"name": "LG UltraGear 27GN950-B", "price": 799.99, "stock": 5},
        {"name": "Dell Alienware AW3423DW", "price": 1299.99, "stock": 3},
    ]
}

# Function to display all PC parts
def display_parts():
    print("\n--- PC Parts Inventory ---")
    for category, items in pc_parts.items():
        print(f"\nCategory: {category}")
        for part in items:
            print(f"  - {part['name']} | Price: ${part['price']} | Stock: {part['stock']}")
    print("\n")

# Function to add a new part
def add_part(category, name, price, stock):
    if category not in pc_parts:
        pc_parts[category] = []
    pc_parts[category].append({"name": name, "price": price, "stock": stock})
    print(f"\nAdded '{name}' to category '{category}'.")

# Function to remove a part
def remove_part(category, name):
    if category in pc_parts:
        for part in pc_parts[category]:
            if part["name"] == name:
                pc_parts[category].remove(part)
                print(f"\nRemoved '{name}' from category '{category}'.")
                return
        print(f"\nPart '{name}' not found in category '{category}'.")
    else:
        print(f"\nCategory '{category}' does not exist.")

# Function to search for a part
def search_part(name):
    print(f"\nSearching for '{name}'...")
    for category, items in pc_parts.items():
        for part in items:
            if part["name"].lower() == name.lower():
                print(f"Found '{name}' in category '{category}' | Price: ${part['price']} | Stock: {part['stock']}")
                return
    print(f"Part '{name}' not found.")

# Function to update stock for a part
def update_stock(category, name, stock):
    if category in pc_parts:
        for part in pc_parts[category]:
            if part["name"] == name:
                part["stock"] = stock
                print(f"\nUpdated stock for '{name}' in category '{category}' to {stock}.")
                return
        print(f"\nPart '{name}' not found in category '{category}'.")
    else:
        print(f"\nCategory '{category}' does not exist.")

# Function to calculate total inventory value
def calculate_inventory_value():
    total_value = 0
    for items in pc_parts.values():
        for part in items:
            total_value += part["price"] * part["stock"]
    print(f"\nTotal Inventory Value: ${total_value:.2f}")

# Example usage
display_parts()
add_part("CPU", "Intel Core i5-13600K", 319.99, 12)
remove_part("GPU", "NVIDIA RTX 4090")
search_part("Corsair Vengeance DDR5 32GB")
update_stock("Storage", "Samsung 980 PRO 2TB SSD", 30)
calculate_inventory_value()
display_parts()
