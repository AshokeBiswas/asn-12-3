1. Multithreading in Python
Multithreading in Python refers to the ability of a program to execute multiple threads concurrently. Each thread is a separate flow of execution, allowing tasks to run in parallel. It is used to improve performance by utilizing multiple CPU cores and handling concurrent tasks like I/O-bound operations effectively.
The module used to handle threads in Python is the threading module. It provides a high-level interface for creating and managing threads.
2. Functions in the threading Module
•	activeCount(): Returns the number of Thread objects currently alive.
•	currentThread(): Returns the current Thread object.
•	enumerate(): Returns a list of all Thread objects currently alive.
3. Functions Related to Threads
•	run(): Defines the entry point for the thread's activity. You override this method in a subclass to implement the specific behavior of the thread.
•	start(): Starts the thread's activity by calling the run() method.
•	join(timeout=None): Waits for the thread to complete. It blocks the calling thread until the thread whose join() method is called terminates or until the optional timeout occurs.
•	isAlive(): Returns whether the thread is alive (i.e., has been started and has not yet terminated).
4. Example Python Program with Two Threads
Here's a Python program that creates two threads:
•	Thread one prints the list of squares.
•	Thread two prints the list of cubes.
python
Copy code
import threading

def print_squares():
    squares = [x * x for x in range(1, 6)]
    print("Squares:", squares)

def print_cubes():
    cubes = [x * x * x for x in range(1, 6)]
    print("Cubes:", cubes)

# Create threads
thread1 = threading.Thread(target=print_squares)
thread2 = threading.Thread(target=print_cubes)

# Start threads
thread1.start()
thread2.start()

# Wait for threads to complete
thread1.join()
thread2.join()

print("Main thread exiting.")
5. Advantages and Disadvantages of Multithreading
Advantages:
•	Concurrency: Allows tasks to run concurrently, utilizing multiple CPU cores.
•	Responsiveness: Improves responsiveness in applications that involve I/O-bound operations.
•	Resource Sharing: Threads within the same process share memory, making data sharing easier and faster.
Disadvantages:
•	Complexity: Synchronization and coordination between threads can lead to complexity and potential bugs (race conditions, deadlocks).
•	Overhead: Creating and managing threads comes with overhead in terms of memory and CPU usage.
•	GIL Limitations: Python's Global Interpreter Lock (GIL) limits true parallelism in CPU-bound tasks.
6. Deadlocks and Race Conditions
•	Deadlock: A deadlock occurs when two or more threads are blocked forever, waiting for each other to release resources that they have locked. For example, Thread A holds Resource X and waits for Resource Y, while Thread B holds Resource Y and waits for Resource X.
•	Race Condition: A race condition occurs when two or more threads or processes attempt to change shared data at the same time. The final outcome of the data depends on the timing of how the threads are scheduled. This can lead to unpredictable and undesirable results.

