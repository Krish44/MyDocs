### SIGTERM (15) :     
	- Default behavior of kill     
	- Ask that process to gracefully shutdown    
	- Ex: kill 123    
    
### SIGQUIT (3):     
	- Makes the OS perform a core dump    
	- core dump is a snapshot of the working memory of the process at the time we sent the kill signal    
	- By default will be written to the current working directory    
	- can use core dumps for debugging purposes.    
	- Ex: kill -3 123    
	    
 ### SIGKILL (9):    
	- can force it to terminate     
	- Ask the kernel to immediately shut down the process.     
	- The process dies and won’t clean up after itself.    
	- There is a risk of data loss or even worse, data corruption.    
	- Ex: kill -9 123    
    
### SIGSTOP (19):    
	- SIGSTOP signal will not terminate a process    
	- equivalent of stopping and putting a process in the background with ctrl+z    
	- Ex: kill -19 123    
	- process can be resumed by sending the continue signal SIGCONT (18)    
	- Ex: kill -18 123    
    
Signal man page: https://man7.org/linux/man-pages/man7/signal.7.html    
