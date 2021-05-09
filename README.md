# Linux_Multi_level_Seheduler
Simulating a Multi Level Scheduler
This project simulates a Multi-Level Scheduler (short term and long term) using the Pthread library.

To implement this I used two threads for each scheduler, I also used two Queues data structure named ready and job and made a struct with PID (unique ID of process) and Time (total execution time of process).

I populated the job Queue with 100 processes. For each process, auto increment (starting from 1) the PID and randomly select Time (in the range 1-30). Display logging message to the screen: “[Kernel] Process X created with Time = Y”.

Invoke the long-term scheduler. Every time long-term scheduler method is invoked, display the logging message: “[Kernel] Long Term Scheduler Invoked” from the main program. First, it will display a logging message to show the current content of the job queue and ready queue as:
“[LTS] Job Queue: [Process X1: Time Y1], ….” “[LTS] Ready Queue: [Process X2: Time Y2], ….” or “[LTS] Ready Queue: EMPTY”
Long-term scheduler method will dequeue an element (process) from the job queue and enqueue it into the ready queue. Display logging message to the screen: “[LTS] Process X removed from the Job Queue and inserted to the Ready Queue”. However, the ready queue has maximum length 5; if the ready queue is full, display logging message to the screen: “[LTS] Ready Queue is Full, cannot enter more”. Long term scheduler will try to insert multiple processes to the queue if there are free spots. Now, Long-term scheduler will again display the content of the two queues using same format as mentioned above and will pass the control to short-term scheduler.

Display the logging message: “[Kernel] Short Term Scheduler Invoked” from the main program; this message will be displayed every time the short term scheduler is invoked. Then, short term scheduler will display the content of two queues using the format discussed earlier, change LTS to STS. Then, short-term scheduler method will dequeue an element (process) from the ready queue and display the logging message to the screen: “[STS] Process X now executing”. It will then reduce its time by two and enqueue it at the end of the ready queue. Also display the logging message to the screen: “[STS] Process X with remaining time Y enqueued to the Ready Queue”. If the message has consumed its entire time, then it will not be enqueued to the ready queue and the logging message will be: “[STS] Process X terminated”
