
	———————————————————————————————————————————————————————————————————————
	CODE IS COLLECTED FOR THE EDUCATIONAL PURPOSE. OCCASIONALLY, I REFACTOR 
	OR WRITE SOME PROTION   
	———————————————————————————————————————————————————————————————————————
	
	
	MULTI-THREADING IN JAVA
	———————————————————————
	
	
	THREAD CLASS METHODS
	————————————————————
	
	public void start(): START A THREAD BY CALLING ITS run() METHOD
	
	public void run(): ENTRY POINT FOR THE THREAD
	
	public final vod setName(String tName): SET THE NAME OF THE THREAD
	
	public final vod setPriority(int tPriority): TO SET THE PRIORITY OF THE THREAD
	
	public final vod setDaemon(BOOLEAN ON): A PARAMETER OF TRUE DENOTES THIS THREAD AS A DAEMON THREAD.
	
	void join(Long miliSec): WAIT FOR A THREAD TO TERMINATE. THIS METHOD WHEN CALLED FROM THE PARENT THREAD MAKES PARENT THREAD WAIT TILL CHILD THREAD TERMINATES. THE CURRENT THREAD INVOKES THIS METHOD ON A SECOND THREAD, CAUSING THE CURRENT THREAD TO BLOCK UNTIL THE SECOND THREAD TERMINATES OR THE SPECIFIED NUMBER OF MILLISECONDS PASSES.
	
	public void interrupt(): INTERRUPTS THIS THREAD, CAUSING IT TO CONTINUE EXECUTION IF IT WAS BLOCKED FOR ANY REASON.
	
	public final boolean isAlive(): DETERMINE IF A THREAD IS STILL RUNNING
	
	
	THE FOLLOWING METHODS IN THE THREAD CLASS ARE STATIC. INVOKING ONE OF THE STATIC METHODS PERFORMS THE OPERATION ON THE CURRENTLY RUNNING THREAD.
	
	public static void yield(): CAUSES THE CURRENTLY RUNNING THREAD TO YIELD TO ANY OTHER THREADS OF THE SAME PRIORITY THAT ARE WAITING TO BE SCHEDULED.
	
	public static void sleep(Long miliSecond): CAUSES THE CURRENTLY RUNNING THREAD TO BLOCK FOR AT LEAST THE SPECIFIED NUMBER OF MILLISECONDS.
	
	public static boolean holdSlock(Object x): RETURNS TRUE IF THE CURRENT THREAD HOLDS THE LOCK ON THE GIVEN OBJECT.
	
	public static Thread currentThread(): RETURNS A REFERENCE TO THE CURRENTLY RUNNING THREAD, WHICH IS THE THREAD THAT INVOKES THIS METHOD.
	
	public static void dumpStack(): PRINTS THE STACK TRACE FOR THE CURRENTLY RUNNING THREAD, WHICH IS USEFUL WHEN DEBUGGING A MULTITHREADED APPLICATION.
	
	getName(): IT IS USED FOR OBTAINING A THREAD’S NAME
	void getPriority(): OBTAIN A THREAD’S PRIORITY
	
	
	MIN_PRIORITY, NORM_PRIORITY OR MAX_PRIORITY.
	
	
	THERE ARE SOME METHODS THAT CAN BE USE BY THE THREADS TO COMMUNICATE WITH EACH OTHER. THEY ARE AS FOLLOWING,
	
	wait(): TELLS THE CALLING THREAD TO GIVE UP THE MONITOR AND GO TO SLEEP UNTIL SOME OTHER THREAD ENTERS THE SAME MONITOR AND CALLS NOTIFY().
	
	notify(): WAKES UP THE FIRST THREAD THAT CALLED WAIT() ON THE SAME OBJECT.
	notifyAll(): WAKES UP ALL THE THREADS THAT CALLED WAIT() ON THE SAME OBJECT. THE HIGHEST PRIORITY THREAD WILL RUN FIRST.
	
	
	JAVA THREAD PRIORITIES ARE IN THE RANGE BETWEEN MIN_PRIORITY (A CONSTANT OF 1) AND MAX_PRIORITY (A CONSTANT OF 10). BY DEFAULT, EVERY THREAD IS GIVEN PRIORITY NORM_PRIORITY (A CONSTANT OF 5). THREADS WITH HIGHER PRIORITY ARE MORE IMPORTANT TO A PROGRAM AND SHOULD BE ALLOCATED PROCESSOR TIME BEFORE LOWER-PRIORITY THREADS. HOWEVER, THREAD PRIORITIES CANNOT GUARANTEE THE ORDER IN WHICH THREADS EXECUTE AND VERY MUCH PLATFORM DEPENDENT.
	
	
	
	THREAD SYNCHRONIZATION
	——————————————————————
	
	WHEN TWO OR MORE THREADS NEED ACCESS TO A SHARED RESOURCE THERE SHOULD BE SOME WAY THAT THE RESOURCE WILL BE USED ONLY BY ONE RESOURCE AT A TIME. THE PROCESS TO ACHIEVE THIS IS CALLED SYNCHRONIZATION. ONCE A THREAD IS INSIDE A SYNCHRONIZED METHOD, NO OTHER THREAD CAN CALL ANY OTHER SYNCHRONIZED METHOD ON THE SAME OBJECT. TO UNDERSTAND SYNCHRONIZATION JAVA HAS A CONCEPT OF MONITOR. MONITOR CAN BE THOUGHT OF AS A BOX WHICH CAN HOLD ONLY ONE THREAD. ONCE A THREAD ENTERS THE MONITOR ALL THE OTHER THREADS HAVE TO WAIT UNTIL THAT THREAD EXITS THE MONITOR.
	
	INTER-THREAD COMMUNICATION
	INTER THREAD COMMUNICATION IS IMPORTANT WHEN YOU DEVELOP AN APPLICATION WHERE TWO OR MORE THREADS EXCHANGE SOME INFORMATION.
	public void wait(): CAUSES THE CURRENT THREAD TO WAIT UNTIL ANOTHER THREAD INVOKES THE NOTIFY().
	public void notify(): WAKES UP A SINGLE THREAD THAT IS WAITING ON THIS OBJECT'S MONITOR.
	public void notifyAll(): WAKES UP ALL THE THREADS THAT CALLED WAIT( ) ON THE SAME OBJECT.
	THESE METHODS HAVE BEEN IMPLEMENTED AS FINAL METHODS IN OBJECT, SO THEY ARE AVAILABLE IN ALL THE CLASSES. ALL 3 METHODS CAN BE CALLED ONLY FROM WITHIN A SYNCHRONIZED CONTEXT.
	THREAD DEADLOCK
	DEADLOCK DESCRIBES A SITUATION WHERE TWO OR MORE THREADS ARE BLOCKED FOREVER, WAITING FOR EACH OTHER. DEADLOCK OCCURS WHEN MULTIPLE THREADS NEED THE SAME LOCKS BUT OBTAIN THEM IN DIFFERENT ORDER. A JAVA MULTITHREADED PROGRAM MAY SUFFER FROM THE DEADLOCK CONDITION BECAUSE THE SYNCHRONIZED KEYWORD CAUSES THE EXECUTING THREAD TO BLOCK WHILE WAITING FOR THE LOCK, OR MONITOR, ASSOCIATED WITH THE SPECIFIED OBJECT.
	
	THREAD CONTROL
	——————————————
	
	CORE JAVA PROVIDES A COMPLETE CONTROL OVER MULTITHREADED PROGRAM. YOU CAN DEVELOP A MULTITHREADED PROGRAM WHICH CAN BE SUSPENDED, RESUMED OR STOPPED COMPLETELY BASED ON YOUR REQUIREMENTS. THERE ARE VARIOUS STATIC METHODS WHICH YOU CAN USE ON THREAD OBJECTS TO CONTROL THEIR BEHAVIOR.
	PUBLIC VOID SUSPEND(): THIS METHOD PUTS A THREAD IN SUSPENDED STATE AND CAN BE RESUMED USING RESUME() METHOD.
	PUBLIC VOID STOP(): THIS METHOD STOPS A THREAD COMPLETELY.
	PUBLIC VOID RESUME(): THIS METHOD RESUMES A THREAD WHICH WAS SUSPENDED USING SUSPEND() METHOD.
	PUBLIC VOID WAIT(): CAUSES THE CURRENT THREAD TO WAIT UNTIL ANOTHER THREAD INVOKES THE NOTIFY().
	PUBLIC VOID NOTIFY(): WAKES UP A SINGLE THREAD THAT IS WAITING ON THIS OBJECT'S MONITOR.
	BE AWARE THAT LATEST VERSIONS OF JAVA HAS DEPRECATED THE USAGE OF SUSPEND(), RESUME() AND STOP() METHODS AND SO YOU NEED TO USE AVAILABLE ALTERNATIVES.
	THREAD LIFE CYCLE AND THREAD SCHEDULING
	THE START METHOD CREATES THE SYSTEM RESOURCES, NECESSARY TO RUN THE THREAD, SCHEDULES THE THREAD TO RUN, AND CALLS THE THREAD’S RUN METHOD.
	A THREAD BECOMES “NOT RUNNABLE” WHEN ONE OF THESE EVENTS OCCURS:
	IF SLEEP METHOD IS INVOKED.
	THE THREAD CALLS THE WAIT METHOD.
	THE THREAD IS BLOCKING ON I/O.
	A THREAD DIES NATURALLY WHEN THE RUN METHOD EXITS.
	
	THREAD SCHEDULING
	EXECUTION OF MULTIPLE THREADS ON A SINGLE CPU, IN SOME ORDER, IS CALLED SCHEDULING.
	IN GENERAL, THE RUNNABLE THREAD WITH THE HIGHEST PRIORITY IS ACTIVE (RUNNING)
	JAVA IS PRIORITY-PREEMPTIVE
	IF A HIGH-PRIORITY THREAD WAKES UP, AND A LOW-PRIORITY THREAD IS RUNNING
	THEN THE HIGH-PRIORITY THREAD GETS TO RUN IMMEDIATELY
	ALLOWS ON-DEMAND PROCESSING
	EFFICIENT USE OF CPU
	TYPES OF SCHEDULING
	WAITING AND NOTIFYING
	WAITING [WAIT()] AND NOTIFYING [NOTIFY(), NOTIFYALL()] PROVIDES MEANS OF COMMUNICATION BETWEEN THREADS THAT SYNCHRONIZE ON THE SAME OBJECT.
	WAIT(): WHEN WAIT() METHOD IS INVOKED ON AN OBJECT, THE THREAD EXECUTING THAT CODE GIVES UP ITS LOCK ON THE OBJECT IMMEDIATELY AND MOVES THE THREAD TO THE WAIT STATE.
	NOTIFY(): THIS WAKES UP THREADS THAT CALLED WAIT() ON THE SAME OBJECT AND MOVES THE THREAD TO READY STATE.
	NOTIFYALL(): THIS WAKES UP ALL THE THREADS THAT CALLED WAIT() ON THE SAME OBJECT.
	RUNNING AND YIELDING
	YIELD() IS USED TO GIVE THE OTHER THREADS OF THE SAME PRIORITY A CHANCE TO EXECUTE I.E. CAUSES CURRENT RUNNING THREAD TO MOVE TO RUNNABLE STATE.
	SLEEPING AND WAKING UP
	NSLEEP() IS USED TO PAUSE A THREAD FOR A SPECIFIED PERIOD OF TIME I.E. MOVES THE CURRENT RUNNING THREAD TO SLEEP STATE FOR A SPECIFIED AMOUNT OF TIME, BEFORE MOVING IT TO RUNNABLE STATE. THREAD.SLEEP(NO. OF MILLISECONDS);
	
	THREAD PRIORITY
	WHEN A JAVA THREAD IS CREATED, IT INHERITS ITS PRIORITY FROM THE THREAD THAT CREATED IT.
	YOU CAN MODIFY A THREAD’S PRIORITY AT ANY TIME AFTER ITS CREATION USING THE SETPRIORITY() METHOD.
	THREAD PRIORITIES ARE INTEGERS RANGING BETWEEN MIN_PRIORITY (1) AND MAX_PRIORITY (10) . THE HIGHER THE INTEGER, THE HIGHER THE PRIORITY.NORMALLY THE THREAD PRIORITY WILL BE 5.
	BLOCKING THREADS
	WHEN READING FROM A STREAM, IF INPUT IS NOT AVAILABLE, THE THREAD WILL BLOCK
	THREAD IS SUSPENDED (“BLOCKED”) UNTIL I/O IS AVAILABLE
	ALLOWS OTHER THREADS TO AUTOMATICALLY ACTIVATE
	WHEN I/O AVAILABLE, THREAD WAKES BACK UP AGAIN
	BECOMES “RUNNABLE” I.E. GETS INTO READY STATE
	GROUPING THREADS
	THREAD GROUPS PROVIDE A MECHANISM FOR COLLECTING MULTIPLE THREADS INTO A SINGLE OBJECT AND MANIPULATING THOSE THREADS ALL AT ONCE, RATHER THAN INDIVIDUALLY.
	TO PUT A NEW THREAD IN A THREAD GROUP THE GROUP MUST
	BE EXPLICITLY SPECIFIED WHEN THE THREAD IS CREATED
	– PUBLIC THREAD(THREADGROUP GROUP, RUNNABLE RUNNABLE)
	– PUBLIC THREAD(THREADGROUP GROUP, STRING NAME)
	– PUBLIC THREAD(THREADGROUP GROUP, RUNNABLE RUNNABLE, STRING NAME)
	A THREAD CAN NOT BE MOVED TO A NEW GROUP AFTER THE THREAD HAS BEEN CREATED.
	WHEN A JAVA APPLICATION FIRST STARTS UP, THE JAVA RUNTIME SYSTEM CREATES A THREADGROUP NAMED MAIN.
	JAVA THREAD GROUPS ARE IMPLEMENTED BY THE JAVA.LANG.THREADGROUP CLASS.
	
	DAEMON THREAD
	DAEMON THREAD IS A LOW PRIORITY THREAD (IN CONTEXT OF JVM) THAT RUNS IN BACKGROUND TO PERFORM TASKS SUCH AS GARBAGE COLLECTION (GC) ETC., THEY DO NOT PREVENT THE JVM FROM EXITING (EVEN IF THE DAEMON THREAD ITSELF IS RUNNING) WHEN ALL THE USER THREADS (NON-DAEMON THREADS) FINISH THEIR EXECUTION. JVM TERMINATES ITSELF WHEN ALL USER THREADS (NON-DAEMON THREADS) FINISH THEIR EXECUTION, JVM DOES NOT CARE WHETHER DAEMON THREAD IS RUNNING OR NOT, IF JVM FINDS RUNNING DAEMON THREAD (UPON COMPLETION OF USER THREADS), IT TERMINATES THE THREAD AND AFTER THAT SHUTDOWN ITSELF.
	# A NEWLY CREATED THREAD INHERITS THE DAEMON STATUS OF ITS PARENT. THAT’S THE REASON ALL THREADS CREATED INSIDE MAIN METHOD (CHILD THREADS OF MAIN THREAD) ARE NON-DAEMON BY DEFAULT, BECAUSE MAIN THREAD IS NON-DAEMON.
	# METHODS OF THREAD CLASS THAT ARE RELATED TO DAEMON THREADS AS FOLLOWING,
	PUBLIC VOID SETDAEMON(BOOLEAN STATUS): THIS METHOD IS USED FOR MAKING A USER THREAD TO DAEMON THREAD OR VICE VERSA. FOR EXAMPLE IF I HAVE A USER THREAD T THEN T.SETDAEMON(TRUE) WOULD MAKE IT DAEMON THREAD. ON THE OTHER HAND IF I HAVE A DAEMON THREAD TD THEN BY CALLING TD.SETDAEMON(FALSE) WOULD MAKE IT NORMAL THREAD(USER THREAD/NON-DAEMON THREAD).
	PUBLIC BOOLEAN ISDAEMON(): THIS METHOD IS USED FOR CHECKING THE STATUS OF A THREAD. IT RETURNS TRUE IF THE THREAD IS DAEMON ELSE IT RETURNS FALSE.
	SETDAEMON(): METHOD CAN ONLY BE CALLED BEFORE STARTING THE THREAD. THIS METHOD WOULD THROW ILLEGALTHREADSTATEEXCEPTION IF YOU CALL THIS METHOD AFTER THREAD.START() METHOD. (REFER THE EXAMPLE)
	THREAD JOIN() METHOD
	THE JOIN() METHOD IS USED TO HOLD THE EXECUTION OF CURRENTLY RUNNING THREAD UNTIL THE SPECIFIED THREAD IS DEAD(FINISHED EXECUTION).
	
	DIFFERENCE BETWEEN CALLING RUN AND START METHOD
	WE CAN CALL RUN() METHOD IF WE WANT BUT THEN IT WOULD BEHAVE JUST LIKE A NORMAL METHOD AND WE WOULD NOT BE ABLE TO TAKE THE ADVANTAGE OF MULTITHREADING. WHEN THE RUN METHOD GETS CALLED THOUGH START() METHOD THEN A NEW SEPARATE THREAD IS BEING ALLOCATED TO THE EXECUTION OF RUN METHOD, SO IF MORE THAN ONE THREAD CALLS START() METHOD THAT MEANS THEIR RUN METHOD IS BEING EXECUTED BY SEPARATE THREADS (THESE THREADS RUN SIMULTANEOUSLY).
	ON THE OTHER HAND IF THE RUN() METHOD OF THESE THREADS ARE BEING CALLED DIRECTLY THEN THE EXECUTION OF ALL OF THEM IS BEING HANDLED BY THE SAME CURRENT THREAD AND NO MULTITHREADING WILL TAKE PLACE, HENCE THE OUTPUT WOULD REFLECT THE SEQUENTIAL EXECUTION OF THREADS IN THE SPECIFIED ORDER.
	
	
	
	————————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	————————————————————————————————————————————————————————————————————————————————————————
	
	———————————————————
	CONCURRENCY CLASSES 
	———————————————————
	
	BlockingQueue
	
	ArrayBlockingQueue
	
	DelayQueue
	
	LinkedBlockingQueue
	
	PriorityBlockingQueue
	
	SynchronousQueue
	
	BlockingDeque
	
	LinkedBlockingDeque
	
	ConcurrentMap
	
	ConcurrentNavigableMap
	
	CountDownLatch
	
	CyclicBarrier
	
	Exchanger
	
	Semaphore
	
	ExecutorService
	
	ThreadPoolExecutor
	
	ScheduledExecutorService
	
	Java Fork and Join using ForkJoinPool
	
	Lock
	
	ReadWriteLock
	
	AtomicBoolean
	
	AtomicInteger
	
	AtomicLong
	
	AtomicReference
	
	AtomicStampedReference
	
	AtomicIntegerArray
	
	AtomicLongArray
	
	AtomicReferenceArray
	————————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	
	
	
	
	
	
	OBJECT LEVEL LOCKING VS. CLASS LEVEL LOCKING IN JAVA
	————————————————————————————————————————————————————
	
	Synchronization refers to multi-threading. A synchronized block of code can only be
	executed by one thread at a time.
	
	Java supports multiple threads to be executed. This may cause two or more threads to
	access the same fields or objects. Synchronization is a process which keeps all concurrent
	threads in execution to be in sync. Synchronization avoids memory consistence errors caused due to inconsistent view of shared memory. When a method is declared as synchronized; the
	thread holds the monitor for that method’s object If another thread is executing the
	synchronized method, your thread is blocked until that thread releases the monitor.
	
	Synchronization in java is achieved using synchronized keyword. You can use synchronized
	keyword in your class on defined methods or blocks. Keyword can not be used with variables
	or attributes in class definition.
	
	
	
	
	OBJECT LEVEL LOCKING
	--------------------
	
	Object level locking is mechanism when you want to synchronize a non-static method or
	non-static code block such that only one thread will be able to execute the code block
	on given instance of the class. This should always be done to make instance level data
	thread safe. This can be done as below :
	
	
	public class DemoClass{
	
	   public synchronized void demoMethod(){}
	}
	
	
	
	OR,
	
	
	public class DemoClass
	{
	   public void demoMethod()
	   {
	       synchronized (this)
	       {
	
	           //other thread safe code
	       }
	   }
	}
	
	
	
	OR,
	
	
	
	public class DemoClass
	{
	
	   private final Object lock = new Object();
	
	   public void demoMethod()
	   {
	       synchronized (lock)
	       {
	           //other thread safe code
	       }
	   }
	}
	
	
	
	
	CLASS LEVEL LOCKING
	-------------------
	
	Class level locking prevents multiple threads to enter in synchronized block in any of
	all available instances on runtime. This means if in runtime there are 100 instances of
	DemoClass, then only one thread will be able to execute demoMethod() in any one of instance
	at a time, and all other instances will be locked for other threads. This should always be
	done to make static data thread safe.
	
	
	public class DemoClass
	{
	   public synchronized static void demoMethod(){}
	}
	
	
	OR,
	
	
	public class DemoClass
	{
	
	   public void demoMethod()
	   {
	
	       synchronized (DemoClass.class)
	       {
	
	           //other thread safe code
	       }
	   }
	}
	
	
	
	OR,
	
	
	
	public class DemoClass
	{
	   private final static Object lock = new Object();
	
	   public void demoMethod()
	   {
	       synchronized (lock)
	       {
	           //other thread safe code
	       }
	   }
	}
	
	
	NOTES
	-----
	
	a. Synchronization in Java guarantees that no two threads can execute a synchronized
	  method which requires same lock simultaneously or concurrently.
	
	b. Synchronized keyword can be used only with methods and code blocks. These methods
	  or blocks can be static or non-static both.
	
	c. When ever a thread enters into java synchronized method or block it acquires a lock
	  and whenever it leaves java synchronized method or block it releases the lock. Lock
	  is released even if thread leaves synchronized method after completion or due to any
	  Error or Exception.
	
	d. Java synchronized keyword is re-entrant in nature it means if a java synchronized method
	  calls another synchronized method which requires same lock then current thread which is
	  holding lock can enter into that method without acquiring lock.
	
	e. Java Synchronization will throw NullPointerException if object used in java synchronized
	  block is null. For example, in above code sample if lock is initialized as null, the
	  synchronized (lock) will throw NullPointerException.
	
	f. Synchronized methods in Java put a performance cost on your application. So use
	  synchronization when it is absolutely required. Also, consider using synchronized
	  code blocks for synchronizing only critical section of your code.
	
	g. It’s possible that both static synchronized and non static synchronized method can
	  run simultaneously or concurrently because they lock on different object.
	
	h. According to the Java language specification you can not use java synchronized keyword
	  with constructor it’s illegal and result in compilation error.
	
	i. Do not synchronize on non final field on synchronized block in Java. because reference of
	  non final field may change any time and then different thread might synchronizing on
	  different objects i.e. no synchronization at all. Best is to use String class, which is
	  already immutable and declared final.
	
	—————————————————————————————————————————————
	
	
	
	
	
	
	
	
	
	————————————————————————————————————————————————————————————————————————————————————————
	
	MULTITHREADED SERVERS IN JAVA <HTTP://TUTORIALS.JENKOV.COM/JAVA-MULTITHREADED-SERVERS/INDEX.HTML>
	
	JAVA IO TUTORIAL <HTTP://TUTORIALS.JENKOV.COM/JAVA-IO/INDEX.HTML>
	
	JAVA NIO TUTORIAL <HTTP://TUTORIALS.JENKOV.COM/JAVA-NIO/INDEX.HTML>
	
	
	
	———————————————————————————————
	JAVA CONCURRENCY - JAKOB JENKOV
	———————————————————————————————
	
	MULTITHREADING BENEFITS
	
	MULTITHREADING COSTS
	
	
	———————————————————————————————————————————————————————————
	——————————————————
	CONCURRENCY MODELS
	——————————————————
	———————————————————————————————————————————————————————————
	CONCURRENCY MODELS AND DISTRIBUTED SYSTEM SIMILARITIES
	
	PARALLEL WORKERS
	
	PARALLEL WORKERS ADVANTAGES
	
	PARALLEL WORKERS DISADVANTAGES
	
	SHARED STATE CAN GET COMPLEX
	
	STATELESS WORKERS
	
	JOB ORDERING IS NONDETERMINISTIC
	
	ASSEMBLY LINE
	
	REACTIVE, EVENT DRIVEN SYSTEMS
	
	ACTORS VS. CHANNELS
	
	ASSEMBLY LINE ADVANTAGES
	
	NO SHARED STATE
	
	STATEFUL WORKERS
	
	BETTER HARDWARE CONFORMITY
	
	JOB ORDERING IS POSSIBLE
	
	ASSEMBLY LINE DISADVANTAGES
	
	FUNCTIONAL PARALLELISM
	———————————————————————————————————————————————————————————
	
	
	SAME-THREADING
	
	CONCURRENCY VS. PARALLELISM
	
	CREATING AND STARTING JAVA THREADS
	
	RACE CONDITIONS AND CRITICAL SECTIONS
	
	THREAD SAFETY AND SHARED RESOURCES
	
	THREAD SAFETY AND IMMUTABILITY
	
	JAVA MEMORY MODEL
	
	JAVA SYNCHRONIZED BLOCKS
	
	JAVA VOLATILE KEYWORD
	
	JAVA THREADLOCAL
	
	THREAD SIGNALING
	
	DEADLOCK
	
	DEADLOCK PREVENTION
	
	STARVATION AND FAIRNESS
	
	NESTED MONITOR LOCKOUT
	
	SLIPPED CONDITIONS
	
	LOCKS IN JAVA
	
	READ / WRITE LOCKS IN JAVA
	
	REENTRANCE LOCKOUT
	
	SEMAPHORES
	
	BLOCKING QUEUES
	
	THREAD POOLS
	
	COMPARE AND SWAP
	
	ANATOMY OF A SYNCHRONIZER
	
	NON-BLOCKING ALGORITHMS
	
	AMDAHL'S LAW
	
	JAVA CONCURRENCY REFERENCES
	————————————————————————————————————————————————————————————————————————————————————————
	
	
	———————————————————————————————————————————————————————————————————————————————————————
	
	
	——————————————————————————————————————————————————————————————————————————————
	
	—————————————————————————————————————————
	JAVA MULTITHREADED SERVERS - JAKOB JENKOV 
	—————————————————————————————————————————
	
	MULTITHREADED SERVERS IN JAVA
	
	SINGLETHREADED SERVER IN JAVA
	
	MULTITHREADED SERVER IN JAVA
	
	THREAD POOLED SERVER
	——————————————————————————————————————————————————————————————————————————————
	
	
	
	————————————————————————————————————————————————————————————————————————————————
	
	———————————————————————————————
	JAVA PERFORMANCE - JAKOB JENKOV 
	———————————————————————————————
	
	MODERN HARDWARE
	
	MEMORY MANAGEMENT FOR PERFORMANCE
	
	JMH - JAVA MICROBENCHMARK HARNESS
	
	JAVA RING BUFFER
	
	JAVA RESIZABLE ARRAY
	
	JAVA FOR VS. SWITCH PERFORMANCE
	
	JAVA ARRAYLIST VS. OPENARRAYLIST PERFORMANCE
	
	JAVA HIGH PERFORMANCE READ PATTERNS
	
	MICRO BATCHING
	————————————————————————————————————————————————————————————————————————————————
	
	
	
	———————————————————————————————
	JAVA NETWORKING - JAKOB JENKOV 
	———————————————————————————————
	
	JAVA NETWORKING: SOCKET
	
	JAVA NETWORKING: SERVERSOCKET
	
	JAVA NETWORKING: UDP DATAGRAMSOCKET
	
	JAVA NETWORKING: URL + URLCONNECTION
	
	JAVA NETWORKING: JarURLConnection
	
	JAVA NETWORKING: INETADDRESS
	
	JAVA NETWORKING: PROTOCOL DESIGN
	———————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	
	JAVA CONCURRENCY - ABHI 
	———————————————————————
	
	JAVA 5 CONCURRENCY - ABHI ON JAVA
	
	JAVA 5 CONCURRENCY: SELECTING LOCKS - ABHI ON JAVA
	
	JAVA 5 CONCURRENCY: SELECTING SYNCHRONIZERS - ABHI ON JAVA
	
	JAVA 5 CONCURRENCY: SYNCHRONIZERS - ABHI ON JAVA
	
	JAVA 5 CONCURRENCY: CONDITIONS - ABHI ON JAVA
	
	JAVA 5 CONCURRENCY: READER-WRITER LOCKS - ABHI ON JAVA
	
	JAVA 5 CONCURRENCY: LOCKS - ABHI ON JAVA
	
	JAVA 5 CONCURRENCY: CALLABLE AND FUTURE - ABHI ON JAVA
	
	JAVA 5 EXECUTORS: THREADPOOL - ABHI ON JAVA
	
	JAVA 5: NEW FEATURES IN CONCURRENCY - ABHI ON JAVA
	
	JAVA: HANDLING INTERRUPTS - ABHI ON JAVA
	————————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	
	————————————————————————————————————————————————————————————————————————————————————————
	JAVA 8 CONCURRENCY TUTORIAL: ATOMIC VARIABLES AND CONCURRENTMAP - BENJAMIN WINTERBERG/ HANOVER, GERMANY
	
	JAVA 8 CONCURRENCY TUTORIAL: SYNCHRONIZATION AND LOCKS - BENJAMIN WINTERBERG/ HANOVER, GERMANY
	
	JAVA 8 CONCURRENCY TUTORIAL: THREADS AND EXECUTORS - BENJAMIN WINTERBERG/ HANOVER, GERMANY
	
	
	JAVA 8 STREAM TUTORIAL - BENJAMIN WINTERBERG/ HANOVER, GERMANY
	
	JAVA 8 TUTORIAL - BENJAMIN WINTERBERG/ HANOVER, GERMANY
	————————————————————————————————————————————————————————————————————————————————————————
	
	
	
	————————————
	APACHE KAFKA
	————————————
	——————————————————————————————————————————————————————————————————————————————————
	APACHE KAFKA SERIES - LEARN APACHE KAFKA FOR BEGINNERS - STEPHANE MAAREK/ UDEMY 
	
	APACHE KAFKA SERIES - KAFKA CONNECT HANDS-ON LEARNING - STEPHANE MAAREK/ UDEMY 
	
	APACHE KAFKA SERIES - KAFKA STREAMS FOR DATA PROCESSING - STEPHANE MAAREK/ UDEMY 
	
	APACHE KAFKA SERIES - KAFKA SECURITY (SSL SASL KERBEROS ACL) - UDEMY 
	
	APACHE KAFKA SERIES - CONFLUENT SCHEMA REGISTRY & REST PROXY - UDEMY 
	
	APACHE KAFKA SERIES - KAFKA CLUSTER SETUP & ADMINISTRATION - STEPHANE MAAREK/ UDEMY 
	
	APACHE KAFKA SERIES - KAFKA MONITORING AND OPERATIONS - UDEMY 
	——————————————————————————————————————————————————————————————————————————————————
	
	
	—————————————————————————————————————————————————————————————————————————————————————
	MEMORY MANAGEMENT
	—————————————————
	
	JAVA MEMORY MANAGEMENT - UDEMY 
	
	A COMPREHENSIVE INTRODUCTION TO JAVA VIRTUAL MACHINE (JVM) - UDEMY 
	
	MEMORY MANAGEMENT AND GARBAGE COLLECTION IN JAVA - LYNDA 
	
	MANAGING THREADS IN JAVA - LYNDA
	—————————————————————————————————————————————————————————————————————————————————————
	
	
	
	—————————————————————————————————————————————————————————————————————————————————————
	MULTITHREADING AND PARALLEL COMPUTATION IN JAVA -  UDEMY/ HOLCZER BALAZS
	
	BYTE SIZE CHUNKS : JAVA MULTITHREADING - UDEMY 
	
	ADVANCED ALGORITHMS IN JAVA -  HOLCZER BALAZS/ UDEMY 
	
	JAVA NETWORK PROGRAMMING - TCP/IP SOCKET PROGRAMMING - UDEMY 
	
	PROFESSIONAL WEB SCRAPING WITH JAVA - UDEMY 
	
	JAVA SOCKET PROGRAMMING: BUILD A CHAT APPLICATION - UDEMY 
	
	COMPLEXITY THEORY BASICS - UDEMY 
	
	INTRO COLLECTIONS, GENERICS AND REFLECTIONS) IN JAVA @ HOLCZER BALAZS
	
	INTRODUCTION TO NUMERICAL METHODS IN JAVA @ HOLCZER BALAZS <HTTPS://WWW.UDEMY.COM/NUMERICAL-METHODS-IN-JAVA/?COUPONCODE=NUMMETHOD_10> 
	—————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	——————————————————————————————————————————————————————————————————————————————
	
	——————————————
	HADOOP COURSES 
	——————————————
	
	JAVA PARALLEL COMPUTATION ON HADOOP - UDEMY 
	
	BUILD BIG DATA PIPELINES W/ HADOOP, FLUME, PIG, MONGODB - UDEMY
	——————————————————————————————————————————————————————————————————————————————
	
	
	EFFICIENT PYTHON FOR HIGH PERFORMANCE PARALLEL COMPUTING - YOUTUBE- ENTHOUGHT/ MIKE MCKERNS
	
	
	—————————————————————————————————————————————————————————————————————————————
	
	
	
	—————————————————————————————————————————————————————————————————————————————
	
	TIM BERGLUND/ CONFLUENT
	———————————————————————
	
	FOUR DISTRIBUTED SYSTEMS ARCHITECTURAL PATTERNS - TIM BERGLUND/ CONFLUENT

	LESSONS LEARNED FORM KAFKA IN PRODUCTION - TIM BERGLUND/ CONFLUENT
	—————————————————————————————————————————————————————————————————————————————


	
	AKKA
	——————
	——————————————————————————————————————————————————
	INTRODUCTION TO AKKA ACTORS WITH JAVA 8 - YOUTUBE 
	——————————————————————————————————————————————————
	
	FUNCTIONAL PROGRAMMING
	——————————————————————
	————————————————————————————————————————————————————————————————
	FUNCTIONAL PROGRAMMING WITH JAVA 8 - YOUTUBE/ VENKAT SUBRAMANIAM
	————————————————————————————————————————————————————————————————
	
	—————————————————————————————————————————————————
	RUSSIAN CONFERENCE ON PARALLEL COMPUTING (JUG.RU)
	—————————————————————————————————————————————————
	
	
	
	LOCKING, FROM TRADITIONAL TO MODERN I, II, III, IV - NIR SHAVIT / YOUTUBE
	
	LOCK-FREE CONCURRENT DATA STRUCTURES I, II, III, IV - DANNY HENDLER/ YOUTUBE
	
	WAIT-FREE COMPUTING "FOR DUMMIES" I, II, III, IV - RACHID GUERRAOUI/ YOUTUBE
	
	RECOMMENDERS AND DISTRIBUTED MACHINE LEARNING I, II - ANNE-MARIE KERMARREC/ YOUTUBE
	
	TRANSACTIONAL MEMORY AND BEYOND I, II, III, IV - MAURICE HERLIHY/ YOUTUBE 
	
	IMPLEMENTATION TECHNIQUES FOR LIBRARIES OF TRANSACTIONAL CONCURRENT DATA TYPES I, II - LIUBA SHRIRA/ YOUTUBE
	
	LOCK-FREE ALGORITHMS FOR KOTLIN COROUTINES I, II - ROMAN ELIZAROV/ YOUTUBE
	
	RELAXED CONCURRENT DATA STRUCTURES I, II, III, IV - DAN ALISTARH /YOUTUBE
	
	UNIVERSAL DISTRIBUTED CONSTRUCTIONS: A GUIDED TOUR I, II  - MICHEL RAYNAL/ YOUTUBE
	
	MEMORY MANAGEMENT FOR CONCURRENT DATA STRUCTURES I, II, III, IV - EREZ PETRANK/ YOUTUBE
	——————————————————————————————————————————————————————————————————————
	
	
	
	
	
	
	——————————————————————————————————————————————————————————————————————
	ADVANCED TOPICS IN PROGRAMMING LANGUAGES: A LOCK-FREE HASH TABLE - GOOGLE TECH ARCHIVE/ YOUTUBE
	DISTRIBUTED OPTIMISTIC ALGORITHM
	SYNCHRONIZATION, ATOMIC OPERATIONS, LOCKS-  CS 162-UC BERKELEY/ YOUTUBE
	
	NON-BLOCKING MICHAEL-SCOTT QUEUE ALGORITHM - ALEXEY FYODOROV/ YOUTUBE
	"DISTRIBUTED, EVENTUALLY CONSISTENT COMPUTATIONS" BY CHRISTOPHER MEIKLEJOHN/ YOUTUBE
	HOW THREADS HELP EACH OTHER - ALEXEY FYODOROV/ YOUTUBE
	
	
	
	GARBAGE COLLECTION IS GOOD!  - INFOQ
	
	G1 GARBAGE COLLECTOR DETAILS AND TUNING - SIMONE BORDET/ YOUTUBE
	
	EVERYTHING I EVER LEARNED ABOUT JVM PERFORMANCE TUNING AT TWITTER - ATTILA SZEGEDI/YOUTUBE
	
	GARBAGE FIRST GARBAGE COLLECTOR  -  MONICA BECKWITH/YOUTUBE
	
	"GC TUNING CONFESSIONS OF A PERFORMANCE ENGINEER"  -  MONICA BECKWITH/YOUTUBE
	
	JVM ( JAVA VIRTUAL MACHINE) ARCHITECTURE - RANJITH RAMACHANDRAN/ YOUTUBE
	GARBAGE COLLECTION IN JAVA, WITH ANIMATION AND DISCUSSION OF G1 GC - RANJITH RAMACHANDRAN/ YOUTUBE
	
	
	LRU CACHE 
	—————————
	THE MAGIC OF LRU CACHE (100 DAYS OF GOOGLE DEV) - GOOGLE DEVELOPERS/ YOUTUBE
	IMPLEMENTING LRU - GEORGIA TECH HPCA III - UDACITY/ YOUTUBE
	
	
	CPU CACHE
	————————— 
	THE MEMORY HIERARCHY - MIT 6.004 L15/ YOUTUBE
	CACHE ISSUES - MIT 6.004 L16/ YOUTUBE
	—————————————————————————————————————————————————————————————————————————————
	
	
	
	
	DIFFERENCE BETWEEN A PROCESS AND A THREAD
	
	
	
	—————————————————————————————————————————————————————————————————————
	JAVA PARALLELISM AND DISTRIBUTED COMPUTING SPECIALIZATION IN COURSERA
	—————————————————————————————————————————————————————————————————————
	
	PARALLEL PROGRAMMING IN JAVA - COURSERA/ RICE UNIVERSITY 
	CONCURRENT PROGRAMMING IN JAVA - COURSERA/ RICE UNIVERSITY 
	DISTRIBUTED PROGRAMMING IN JAVA - COURSERA/ RICE UNIVERSITY 
	—————————————————————————————————————————————————————————————————————
	



	DECENTRALIZED APPLICATIONS - SIRAJ RAVAL/ THE SCHOOL OF AI 
	
	—————————————————————————————————————————————————————————————————————
	EDX COURSERS 
	————————————
	
	RELIABLE DISTRIBUTED ALGORITHMS I & II - KTH/ EDX + YOUTUBE 
	
	DISTRIBUTED MACHINE LEARNING WITH APACHE SPARK - UC BERKELEY/ EDX 
	
	ARCHITECTING DISTRIBUTED CLOUD APPLICATIONS - MICROSOFT/ EDX 
	—————————————————————————————————————————————————————————————————————
	
	
	
	—————————————————————————————————————————————————————————————————————
	
	PARALLEL COMPUTER ARCHITECTURE - PROF. ONUR MUTLU, CMU/ YOUTUBE 
	—————————————————————————————————————————————————————————
	
	
	L-1  INTRODUCTION
	
	L-2  PARALLELISM BASICS 
	
	L-3  PROGRAMMING MODELS
	
	L-4  MULTI-CORE PROCESSORS
	
	L-5  MULTI-CORE PROCESSORS II 
	
	L-6  ASYMMETRY
	
	L-7  EMERGING MEMORY
	
	L-8  MORE ASYMMETRY
	
	L-9  MULTITHREADING
	
	L-10  MULTITHREADING II
	
	L-11 CACHES IN MULTICORES
	
	L-12 CACHING IN MULTI-CORE
	
	L-13 MULTI-THREADING II
	
	L-14 
	
	L-15 SPECULATION 1
	
	L-16
	
	L-17 INTERCONNECTION NETWORKS I
	
	L-18 INTERCONNECTION NETWORKS II
	
	L-19
	
	L-20 SPECULATION+INTERCONNECT III
	
	L-21 INTERCONNECTS IV
	
	L-22 DATAF-LOW I
	
	L-23 DATAFLOW II
	
	L-24-MAIN MEMORY I
	
	L-25 MAIN MEMORY II
	
	L-26 MEMORY INTERFERENCE
	
	L-27 MAIN MEMORY III
	—————————————————————————————————————————————————————————————————————
	
	
	
	
	—————————————————————————————————————————————————————————————————————
	MULTI-CORE PROGRAMMING PRIMER - MIT OPEN COURSEWARE
	
	DISTRIBUTED ALGORITHMS - MIT OCW
	
	PROBABILISTIC SYSTEMS ANALYSIS AND APPLIED PROBABILITY - MIT OCW
	—————————————————————————————————————————————————————————————————————
	
	
	
	
	
	CORE JAVA CONCURRENCY <HTTPS://DZONE.COM/REFCARDZ/CORE-JAVA-CONCURRENCY>
	
	JAVA / CONCURRENCY <HTTP://TUTORIALS.JENKOV.COM/JAVA-CONCURRENCY/JAVA-MEMORY-MODEL.HTML>
	
	CRUNCHIFY JAVA MULTI-THREADING <CRUNCHIFY.COM>
	
	HIGH PERFORMANCE JAVA PERSISTENCE 
	
	ASYNCHRONOUS PROGRAMMING IN JAVA  <HTTPS://CODING2FUN.WORDPRESS.COM/2016/08/09/ASYNCHRONOUS-PROGRAMMING-IN-JAVA/>
	
	A GENTLE GUIDE TO ASYNCHRONOUS PROGRAMMING WITH ECLIPSE VERT.X FOR JAVA DEVELOPERS
	
	HIGHER-ORDER FUNCTIONS, FUNCTIONS COMPOSITION, AND CURRYING IN JAVA 
	
	JAVA DISTRIBUTED COMPUTING - JIM FARLEY/ O'REILLY MEDIA
	
	
	
	
	
	————————————————————————————————————————————————————————
	HIGH PERFORMANCE COMPUTING - GEORGIA TECH/ UDACITY
	
	HIGH PERFORMANCE COMPUTER ARCHITECTURE - GEORGIA TECH/ UDACITY 
	
	INTRO TO PARALLEL TO PROGRAMMING (NIVIDA CUDA) - UDACITY 
	————————————————————————————————————————————————————————
	
	
	
	
	CLOUDS, DISTRIBUTED SYSTEMS, NETWORKING SERIES - UNIVERSITY OF ILLINOIS/ COURSERA 
	—————————————————————————————————————————————————————————————————————————————————
	
	CLOUD COMPUTING CONCEPTS, PART 1 - UNI. OF ILLINOIS/ COURSERA 
	
	CLOUD COMPUTING CONCEPTS: PART 2 - UNI. OF ILLINOIS/ COURSERA 
	
	CLOUD COMPUTING APPLICATIONS, PART 1: CLOUD SYSTEMS AND INFRASTRUCTURE - UNI. OF ILLINOIS/ COURSERA 
	
	CLOUD COMPUTING APPLICATIONS, PART 2: BIG DATA AND APPLICATIONS IN THE CLOUD - UNI. OF ILLINOIS/ COURSERA 
	
	CLOUD NETWORKING - UNI. OF ILLINOIS/ COURSERA 
	
	CLOUD COMPUTING PROJECT - UNI. OF ILLINOIS/ COURSERA 
	
	
	
	
	
	
	
	
	———————————————————————————————————————————————————————————————————————————————————————
	————————————————————
	COMPUTER ARCHITEKTUR
	————————————————————
	———————————————————————————————————————————————————————————————————————————————————————
	COMPUTER ARCHITECTURE - COURSERA/ PRINCETON UNIVERSITY
	
	COMPUTER SYSTEM ARCHITECTURE - MIT OPEN COURSEWARE 
	
	COMPILERS - STANFORD UNIVERSITY 
	
	COMPILERS: THEORY AND PRACTICE - UDACITY
	
	INTRODUCTION TO OPERATING SYSTEMS - UDACITY
	
	ADVANCED OPERATING SYSTEMS - UDACITY
	
	HIGH PERFORMANCE COMPUTER ARCHITECTURE - UDACITY
	
	BUILD A MODERN COMPUTER FROM FIRST PRINCIPLES: FROM NAND TO TETRIS (PROJECT-CENTERED COURSE) - COURSERA 
	———————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	——————————————————————————————————————————————————————————————————————————————————————
	
	JAVA THEORY AND PRACTICES - IBM SERIES 
	——————————————————————————————————————
	
	ARE ALL STATEFUL WEB APPLICATIONS BROKEN?
	
	GOING WILD WITH GENERICS I & II
	
	STICK A FORK IN IT - I & II
	
	MANAGING VOLATILITY
	
	THE CLOSURES DEBATE
	
	USING JAVA 5 LANGUAGE FEATURES IN EARLIER JDKS
	
	INSTRUMENTING APPLICATIONS WITH JMX
	
	TESTING WITH LEVERAGE I, II & III
	
	DEALING WITH INTERRUPTEDEXCEPTION
	
	INTRODUCTION TO NONBLOCKING ALGORITHMS
	
	GOOD HOUSEKEEPING PRACTICES
	
	THE PSEUDO-TYPEDEF ANTIPATTERN
	
	PLUGGING MEMORY LEAKS WITH SOFT REFERENCES
	
	PLUGGING MEMORY LEAKS WITH WEAK REFERENCES
	
	SYNCHRONIZATION OPTIMIZATIONS IN MUSTANG
	
	URBAN PERFORMANCE LEGENDS, REVISITED
	
	DECORATING WITH DYNAMIC PROXIES
	
	BE A GOOD (EVENT) LISTENER
	
	MAKE DATABASE QUERIES WITHOUT THE DATABASE
	
	ENABLE INITIALIZATION ATOMICITY
	
	SCREEN-SCRAPING WITH XQUERY
	
	ANATOMY OF A FLAWED MICROBENCHMARK
	
	GENERICS GOTCHAS
	
	DYNAMIC COMPILATION AND PERFORMANCE MEASUREMENT
	
	GOING ATOMIC
	
	MORE FLEXIBLE, SCALABLE LOCKING IN JDK 5.0
	
	STATE REPLICATION IN THE WEB TIER
	
	KILL BUGS DEAD
	
	THE EXCEPTIONS DEBATE
	
	FIXING THE JAVA MEMORY MODEL I & II
	
	GARBAGE COLLECTION AND PERFORMANCE
	
	GARBAGE COLLECTION IN THE HOTSPOT JVM
	
	A BRIEF HISTORY OF GARBAGE COLLECTION
	
	CHARACTERIZING THREAD SAFETY
	
	BUILDING A BETTER HASHMAP
	
	CONCURRENT COLLECTIONS CLASSES
	
	WHOSE OBJECT IS IT, ANYWAY?
	
	HASHING IT OUT
	
	URBAN PERFORMANCE LEGENDS
	
	PERFORMANCE MANAGEMENT -- DO YOU HAVE A PLAN?
	
	TO MUTATE OR NOT TO MUTATE?
	
	WHERE'S YOUR POINT?
	
	CONCURRENCY MADE SIMPLE (SORT OF)
	
	IS THAT YOUR FINAL ANSWER?
	
	HEY, WHERE'D MY THREAD GO?
	
	I HAVE TO DOCUMENT THAT?
	
	THREAD POOLS AND WORK QUEUES
	
	SAFE CONSTRUCTION TECHNIQUES
	
	UNDERSTANDING JTS -- BALANCING SAFETY AND PERFORMANCE
	
	UNDERSTANDING JTS -- THE MAGIC BEHIND THE SCENES
	
	UNDERSTANDING JTS -- AN INTRODUCTION TO TRANSACTIONS
	
	SHOULD YOU USE JMS IN YOUR NEXT ENTERPRISE APPLICATION?
	——————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	BLOG POSTS, WEB PAGES 
	—————————————————————
	
	
	LINEARIZABILITY, SERIALIZABILITY, TRANSACTION ISOLATION AND CONSISTENCY MODELS - DDDPAUL.GITHUB.IO
	
	LINEARIZABILITY VERSUS SERIALIZABILITY - PETER BAILIS
	
	DISTRIBUTED CONSISTENCY AND SESSION ANOMALIES - BLOG.ACOLYER.ORG
	
	A CRITIQUE OF ANSI SQL ISOLATION LEVELS - BLOG.ACOLYER.ORG
	
	STRONG CONSISTENCY MODELS - APHYR.COM
	
	A BEGINNER’S GUIDE TO DATABASE LOCKING AND THE LOST UPDATE PHENOMENA - VLAD MIHALCEA
	
	GENERALIZED ISOLATION LEVEL DEFINITIONS - BLOG.ACOLYER.ORG
	
	TRANSACTION ISOLATION - POSTGRESQL.ORG
	
	
	TOP 10 ALGORITHMS AND DATA STRUCTURES FOR COMPETITIVE PROGRAMMING [GEEKS FOR GEEKS ] <HTTP://WWW.GEEKSFORGEEKS.ORG/TOP-ALGORITHMS-AND-DATA-STRUCTURES-FOR-COMPETITIVE-PROGRAMMING/> 
	
	JAVA CONCURRENCY @ ORACLE <HTTP://DOCS.ORACLE.COM/JAVASE/TUTORIAL/ESSENTIAL/CONCURRENCY/>
	
	NETWORKING USING JAVA (CHAT MESSENGER) @ BUCKY ROBERTS JAVA INTERMEDIATE TUTORIAL (THE NEW BOSTON)
	
	JAVA CONCURRENCY ESSENTIAL - JAVACODEGEEKS <HTTP://WWW.JAVACODEGEEKS.COM/2015/09/JAVA-
	CONCURRENCY-ESSENTIALS.HTML>
	
	JAVA ANNOTATION TUTORIAL - JAVACODEGEEKS<HTTP://WWW.JAVACODEGEEKS.COM/2014/11/JAVA-ANNOTATIONS-TUTORIAL.HTML>
	
	META-ANNOTATIONS IN JAVA
	
	CUSTOM NETWORKING <HTTP://DOCS.ORACLE.COM/JAVASE/TUTORIAL/NETWORKING/TOC.HTML>
	
	CRUNCHIFY JAVA MULTI-THREADING <CRUNCHIFY.COM>
	
	HIGH PERFORMANCE JAVA PERSISTENCE 
	
	ASYNCHRONOUS PROGRAMMING IN JAVA  <HTTPS://CODING2FUN.WORDPRESS.COM/2016/08/09/ASYNCHRONOUS-PROGRAMMING-IN-JAVA/>
	
	A GENTLE GUIDE TO ASYNCHRONOUS PROGRAMMING WITH ECLIPSE VERT.X FOR JAVA DEVELOPERS
	
	HIGHER-ORDER FUNCTIONS, FUNCTIONS COMPOSITION, AND CURRYING IN JAVA 8 - DZONE
	
	
	
	
	
	OPTIMIZATION 
	————————————
	
	OPTIMIZE THE JAVA CODE - JOOQ.ORG <HTTPS://BLOG.JOOQ.ORG/2015/02/05/TOP-10-EASY-PERFORMANCE-OPTIMISATIONS-IN-JAVA/>
	
	MAKE FAST JAVA <HTTP://WWW.JAVAWORLD.COM/ARTICLE/2077647/BUILD-CI-SDLC/MAKE-JAVA-FAST--OPTIMIZE-.HTML?PAGE=1>
	
	
	JAVA PERFORMANCE
	————————————————
	NETTY, VERT.X, QBIT, JCTOOLS AND CHRONICLE
	
	
	
	
	
	DISTRIBUTED SYSTEMS ARCHITECTURE
	————————————————————————————————
	
	SOFTWARE ARCHITECTURE   
	
	ION   
	
	IAP   
	
	IAP TOOLS FOR JAVA  
	
	GRID OPS FOR JAVA  
	
	SOA - SERVICE ORIENTED ARCHITECTURE   
	
	WEB SERVICES   
	
	SOAP   
	
	WSDL 2.0   
	
	RSYNC   
	
	PEER-TO-PEER (P2P) NETWORKS   
	
	
	——————————————————————————————————————
	YOUTUBE JAVA CHANNEL - YEGOR BUGAYENKO
	——————————————————————————————————————
	
	
	
	
	—————
	BOOKS 
	—————
	
	————————————————————————————————————————————————————————————————————————————————————————
	CONCURRENT PROGRAMMING IN JAVA: DESIGN PRINCIPLES AND PATTERNS - DOUG LEA 
	
	JAVA CONCURRENCY IN PRACTICE - BRIAN GOETZ
	
	CONCURRENCY MODELS IN 7 WEEKS: WHEN THREADS UNRAVEL - PAUL BUTCHER 
	
	JAVA 8 IN ACTION: LAMBDAS, STREAMS, AND FUNCTIONAL-STYLE PROGRAMMING - ALAN MYCROFT, MARIO FUSCO
	
	DISTRIBUTED ALGORITHMS BY PROF. NANCY LYNCH
	
	JAVA PERFORMANCE: THE DEFINITIVE GUIDE - SCOTT OAKS
	
	JAVA PERFORMANCE TUNING - JACK SHIRAZI 
	
	PROGRAMMING FOR THE JAVA™ VIRTUAL MACHINE - JOSHUA ENGEL
	
	DESIGNING DISTRIBUTED SYSTEMS: PATTERNS AND PARADIGMS FOR SCALABLE, RELIABLE SERVICES - BRENDAN BURNS/ OREILLY
	
	DESIGNING DATA-INTENSIVE APPLICATIONS: THE BIG IDEAS BEHIND RELIABLE, SCALABLE, AND MAINTAINABLE SYSTEMS - MARTIN KLEPPMANN
	
	KUBERNETES: UP AND RUNNING: DIVE INTO THE FUTURE OF INFRASTRUCTURE - KELSEY HIGHTOWER, BRENDAN BURNS, JOE BEDA
	
	JAVA DISTRIBUTED COMPUTING - JIM FARLEY/ O'REILLY MEDIA
	
	BUILDING REACTIVE MICROSERVICES IN JAVA BY CLEMENT ESCOER (OREILLY)
	ASYNCHRONOUS AND EVENT-BASED APPLICATION DESIGN
	
	JAVA NETWORK PROGRAMMING: DEVELOPING NETWORKED APPLICATIONS - ELLIOTTE HAROLD
	
	APACHE MAHOUT: BEYOND MAPREDUCE - DMITRIY LYUBIMOV, ANDREW PALUMBO 
	
	MAPREDUCE DESIGN PATTERNS: BUILDING EFFECTIVE ALGORITHMS AND ANALYTICS FOR HADOOP AND OTHER SYSTEMS - DONALD MINER, ADAM SHOOK
	————————————————————————————————————————————————————————————————————————————————————————
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	