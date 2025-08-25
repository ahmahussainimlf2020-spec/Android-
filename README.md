tasks = []

def show_menu():
    print("\n--- To-Do List Menu ---")
    print("1. View tasks")
    print("2. Add task")
    print("3. Remove task")
    print("4. Mark task as done")
    print("5. Exit")

def view_tasks():
    if not tasks:
        print("\nYour to-do list is empty.")
    else:
        print("\n--- Your Tasks ---")
        for i, task in enumerate(tasks, start=1):
            status = "✅" if task['done'] else "❌"
            print(f"{i}. {task['title']} [{status}]")

def add_task():
    title = input("\nEnter task: ")
    tasks.append({"title": title, "done": False})
    print(f"Task '{title}' added.")

def remove_task():
    view_tasks()
    try:
        task_num = int(input("\nEnter task number to remove: ")) - 1
        removed = tasks.pop(task_num)
        print(f"Removed task: {removed['title']}")
    except (IndexError, ValueError):
        print("Invalid choice.")

def mark_done():
    view_tasks()
    try:
        task_num = int(input("\nEnter task number to mark as done: ")) - 1
        tasks[task_num]['done'] = True
        print(f"Task '{tasks[task_num]['title']}' marked as done.")
    except (IndexError, ValueError):
        print("Invalid choice.")

def main():
    while True:
        show_menu()
        choice = input("\nEnter your choice: ")

        if choice == "1":
            view_tasks()
        elif choice == "2":
            add_task()
        elif choice == "3":
            remove_task()
        elif choice == "4":
            mark_done()
        elif choice == "5":
            print("Goodbye! 👋")
            break
        else:
            print("Invalid choice
