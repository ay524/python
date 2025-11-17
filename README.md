class FamilyMember:
    def __init__(self, name, relation, generation=0):
        self.name = name
        self.relation = relation
        self.generation = generation
    
    def introduce(self):
        return f"I am {self.name}, your {self.relation}"
    
    def get_generation_prefix(self):
        prefixes = {
            0: "👤",  # Self
            1: "👨‍👩‍👧",  # Parents, Aunts, Uncles
            2: "🧓"   # Grandparents
        }
        return prefixes.get(self.generation, "👥")

def display_family_tree():
    """Display the complete family tree"""
    
    # Grandparents Generation (Generation 2)
    paternal_grandfather = FamilyMember("Teferi", "paternal grandfather", 2)
    paternal_grandmother = FamilyMember("Yamralu", "paternal grandmother", 2)
    maternal_grandfather = FamilyMember("Tadele", "maternal grandfather", 2)
    maternal_grandmother = FamilyMember("Lkye", "maternal grandmother", 2)
    
    # Parents Generation (Generation 1)
    father = FamilyMember("Birhan", "father", 1)
    mother = FamilyMember("Tenna", "mother", 1)
    
    # Aunts and Uncles (Generation 1)
    # Maternal side (mother's siblings)
    maternal_aunt = FamilyMember("Yadegdgu", "maternal aunt", 1)
    maternal_uncle = FamilyMember("Mengstie", "maternal uncle", 1)
    
    # Paternal side (father's siblings)  
    paternal_aunt = FamilyMember("Emebet", "paternal aunt", 1)
    paternal_uncle = FamilyMember("Aweke", "paternal uncle", 1)
    
    # Self Generation (Generation 0)
    myself = FamilyMember("Ayalsew", "self", 0)
    sister = FamilyMember("Ntsuh", "sister", 0)
    brother = FamilyMember("Fetene", "brother", 0)
    
    print("=" * 60)
    print("🏛️  FAMILY TREE OF AYALSEW")
    print("=" * 60)
    
    # Display family tree in hierarchical order
    print("\n🎯 GENERATION 2 - GRANDPARENTS:")
    print(f"{paternal_grandfather.get_generation_prefix()} {paternal_grandfather.introduce()}")
    print(f"{paternal_grandmother.get_generation_prefix()} {paternal_grandmother.introduce()}")
    print(f"{maternal_grandfather.get_generation_prefix()} {maternal_grandfather.introduce()}")
    print(f"{maternal_grandmother.get_generation_prefix()} {maternal_grandmother.introduce()}")
    
    print("\n🎯 GENERATION 1 - PARENTS & SIBLINGS:")
    print(f"{father.get_generation_prefix()} {father.introduce()}")
    print(f"{mother.get_generation_prefix()} {mother.introduce()}")
    
    print("\n   👨‍👩‍👧‍👦 MATERNAL AUNTS/UNCLES (Mother's side):")
    print(f"   👩 {maternal_aunt.introduce()}")
    print(f"   👨 {maternal_uncle.introduce()}")
    
    print("\n   👨‍👩‍👧‍👦 PATERNAL AUNTS/UNCLES (Father's side):")
    print(f"   👩 {paternal_aunt.introduce()}")
    print(f"   👨 {paternal_uncle.introduce()}")
    
    print(f"\n🎯 GENERATION 0 - SELF:")
    print(f"{myself.get_generation_prefix()} {myself.introduce()}")
    print(f"   👧 {sister.introduce()}")
    print(f"   👦 {brother.introduce()}")

def show_lineage_paths():
    """Show the direct lineage paths from grandparents to yourself"""
    
    print("\n" + "=" * 60)
    print("🔄 DIRECT LINEAGE PATHS")
    print("=" * 60)
    
    print("\n📜 PATERNAL LINEAGE:")
    print("Teferi (paternal grandfather) → Birhan (father) → Ayalsew (you)")
    print("Yamralu (paternal grandmother) → Birhan (father) → Ayalsew (you)")
    
    print("\n📜 MATERNAL LINEAGE:")
    print("Tadele (maternal grandfather) → Tenna (mother) → Ayalsew (you)")
    print("Lkye (maternal grandmother) → Tenna (mother) → Ayalsew (you)")
    
    print("\n👨‍👩‍👧‍👦 EXTENDED FAMILY PATHS:")
    print("Tadele & Lkye (maternal grandparents) → Yadegdgu (maternal aunt)")
    print("Tadele & Lkye (maternal grandparents) → Mengstie (maternal uncle)")
    print("Teferi & Yamralu (paternal grandparents) → Emebet (paternal aunt)")
    print("Teferi & Yamralu (paternal grandparents) → Aweke (paternal uncle)")

def relationship_lookup(name):
    """Look up the relationship of any family member"""
    
    relationships = {
        "teferi": {"relation": "paternal grandfather", "side": "paternal"},
        "yamralu": {"relation": "paternal grandmother", "side": "paternal"},
        "tadele": {"relation": "maternal grandfather", "side": "maternal"},
        "lkye": {"relation": "maternal grandmother", "side": "maternal"},
        "birhan": {"relation": "father", "side": "paternal"},
        "tenna": {"relation": "mother", "side": "maternal"},
        "yadegdgu": {"relation": "maternal aunt", "side": "maternal"},
        "mengstie": {"relation": "maternal uncle", "side": "maternal"},
        "emebet": {"relation": "paternal aunt", "side": "paternal"},
        "aweke": {"relation": "paternal uncle", "side": "paternal"},
        "ayalsew": {"relation": "self", "side": "self"},
        "ntsuh": {"relation": "sister", "side": "self"},
        "fetene": {"relation": "brother", "side": "self"}
    }
    
    lower_name = name.lower().strip()
    
    if lower_name in relationships:
        info = relationships[lower_name]
        return f"🔍 {name.title()} is your {info['relation']} ({info['side']} side)"
    else:
        return f"❌ {name} not found in family records"

def get_family_members_by_side(side):
    """Get all family members from a specific side (paternal/maternal)"""
    
    paternal_family = {
        "Teferi": "paternal grandfather",
        "Yamralu": "paternal grandmother", 
        "Birhan": "father",
        "Emebet": "paternal aunt",
        "Aweke": "paternal uncle"
    }
    
    maternal_family = {
        "Tadele": "maternal grandfather",
        "Lkye": "maternal grandmother",
        "Tenna": "mother",
        "Yadegdgu": "maternal aunt",
        "Mengstie": "maternal uncle"
    }
    
    if side.lower() == "paternal":
        return paternal_family
    elif side.lower() == "maternal":
        return maternal_family
    else:
        return {}

def show_family_connections():
    """Show how all family members are connected"""
    
    print("\n" + "=" * 60)
    print("🔗 FAMILY CONNECTIONS")
    print("=" * 60)
    
    print("\n🌳 MATERNAL FAMILY BRANCH:")
    print("Tadele (maternal grandfather) + Lkye (maternal grandmother)")
    print("  ├── Tenna (your mother)")
    print("  ├── Yadegdgu (maternal aunt)") 
    print("  └── Mengstie (maternal uncle)")
    
    print("\n🌳 PATERNAL FAMILY BRANCH:")
    print("Teferi (paternal grandfather) + Yamralu (paternal grandmother)")
    print("  ├── Birhan (your father)")
    print("  ├── Emebet (paternal aunt)")
    print("  └── Aweke (paternal uncle)")
    
    print("\n💑 YOUR IMMEDIATE FAMILY:")
    print("Birhan (father) + Tenna (mother)")
    print("  ├── Ayalsew (you)")
    print("  ├── Ntsuh (sister)")
    print("  └── Fetene (brother)")

def main():
    """Main function to run the family relationship program"""
    
    # Display complete family tree
    display_family_tree()
    
    # Show lineage paths
    show_lineage_paths()
    
    # Show family connections
    show_family_connections()
    
    # Interactive relationship lookup
    print("\n" + "=" * 60)
    print("🔎 RELATIONSHIP LOOKUP TOOL")
    print("=" * 60)
    
    # Test lookup with all known family members
    family_names = ["Teferi", "Yamralu", "Tadele", "Lkye", "Birhan", "Tenna", 
                   "Yadegdgu", "Mengstie", "Emebet", "Aweke", "Ayalsew",
                   "Ntsuh", "Fetene"]
    
    print("\nTesting with all family members:")
    for name in family_names:
        print(f"  {relationship_lookup(name)}")
    
    # Show family by sides
    print("\n" + "=" * 60)
    print("👨‍👩‍👧‍👦 FAMILY GROUPED BY SIDE")
    print("=" * 60)
    
    print("\nPaternal Family Members:")
    paternal_members = get_family_members_by_side("paternal")
    for name, relation in paternal_members.items():
        print(f"  👨 {name} - {relation}")
    
    print("\nMaternal Family Members:")
    maternal_members = get_family_members_by_side("maternal")
    for name, relation in maternal_members.items():
        print(f"  👩 {name} - {relation}")
    
    # Interactive lookup
    print("\n" + "=" * 60)
    print("💬 INTERACTIVE LOOKUP (Enter 'quit' to exit)")
    print("=" * 60)
    
    while True:
        user_input = input("\nEnter a family member's name to lookup: ").strip()
        
        if user_input.lower() == 'quit':
            print("Thank you for exploring the family tree! 👋")
            break
        
        if user_input:
            print(relationship_lookup(user_input))

# Run the program
if __name__ == "__main__":
    main()
