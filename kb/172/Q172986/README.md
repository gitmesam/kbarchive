---
layout: page
title: "Q172986: INFO: Microsoft Visual Basic 5.0 Service Pack 2 Release Notes"
permalink: /kb/172/Q172986/
---

## Q172986: INFO: Microsoft Visual Basic 5.0 Service Pack 2 Release Notes

{% raw %}

	Article: Q172986
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,97sp2
	Operating System(s): 
	Keyword(s): kbVBp500 kbVS97sp2fix kbvbp500sp2fix
	Last Modified: 18-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This document is copied from VB5SP2.htm that is placed in the Visual Basic 5.0
	directory on your machine when you install Visual Basic 5.0 Service Pack 2.
	Visual Basic 5.0 Service Pack 2 is an update to Visual Basic Professional,
	Enterprise, and Control Creation editions.
	
	MORE INFORMATION
	================
	
	Microsoft Visual Basic 5.0 Service Pack 2 Release Notes
	-------------------------------------------------------
	
	Visual Basic 5.0 Service Pack 2 is an update to Visual Basic Professional,
	Enterprise, and Control Creation editions. It enables apartment-model threading
	for Visual Basic projects that contain user interface elements, such as forms
	and controls. It also fixes several bugs that have been reported in Visual Basic
	5.0. (Search for VB5FixListSP2 on the Knowledge Base Web site at:
	http://msdn.microsoft.com/support.)
	
	Applying Visual Basic 5.0 Service Pack 2 to your licensed copy of Visual Basic
	allows you to create ActiveX controls and ActiveX documents that perform well in
	multithreaded clients like Internet Explorer 4.0. If you have the Professional
	or Enterprise Edition of Visual Basic, you can also create:
	
	- Apartment-threaded DLLs that show forms.
	
	- Multithreaded components that employ ActiveX designers, such as the
	  UserConnection designer.
	
	- Multithreaded client applications to test these components.
	
	This apartment-model threading enhancement is the only feature of Visual Basic
	5.0 Service Pack 2.
	
	These release notes contain information supplementing the Microsoft Visual Basic
	5.0 documentation in Help and Books Online. For additional information, visit
	the Microsoft Visual Basic Web site at:
	
	  http://www.microsoft.com/vbasic/
	
	Overview of Changes to Apartment-Model Threading
	------------------------------------------------
	
	Projects authored with Visual Basic 5.0 Service Pack 2 can take advantage of
	apartment-model threading without having to suppress visual elements such as
	forms and controls. Applying Visual Basic 5.0 Service Pack 2 makes Forms,
	UserControls, UserDocuments, and ActiveX Designers thread-safe:
	
	- Apartment-threaded versions of all the ActiveX controls shipped with Visual
	  Basic 5.0, except: DBGrid, MSChart, and any legacy controls that were
	  included in the Tools directory for backward compatibility.
	
	- An apartment-threaded version of the UserConnection ActiveX designer.
	
	- A new Threading Model option that allows you to recompile your ActiveX
	  control and ActiveX document projects as apartment-threaded .ocx and .dll
	  files.
	
	NOTE: The support code for ActiveX designers is now apartment-model thread- safe,
	but this does not guarantee that a particular designer is thread- safe. If
	you're using a third-party designer, you should check with your vendor.
	
	Limitations of the Control Creation Edition, version 5.0
	--------------------------------------------------------
	
	The only parts of this document that apply to the Control Creation Edition are
	those that affect thread-safe ActiveX control projects.
	
	If you use the Control Creation Edition to create apartment-threaded ActiveX
	controls, you must use a multithreaded client such as Internet Explorer 4.0 to
	test the multithreaded behavior of your controls. You cannot use the Control
	Creation Edition to create a multithreaded test client.
	
	Selecting a Threading Model for Your Project
	--------------------------------------------
	
	Visual Basic 5.0 Service Pack 2 changes the options on the General tab of the
	Project Properties dialog box. After you apply Visual Basic 5.0 Service Pack 2,
	the Unattended Execution option is no longer coupled to the threading model for
	your project. You can select a setting for the Threading Model option without
	marking your project for Unattended Execution.
	
	To set the threading model for an ActiveX DLL, ActiveX Exe, or ActiveX Control
	project:
	
	1. From the Project menu, click <project> Properties to open the Project
	  Properties dialog box.
	
	2. On the General tab, select the desired options in the Threading Model box.
	
	For ActiveX DLL and ActiveX Control projects, you can select either
	Apartment-Threaded or Single-Threaded.
	
	For ActiveX Exe projects, you can either specify that each new object is created
	on a new thread (Thread per Object), or limit your component to a fixed pool of
	threads. A thread pool size of one (1) makes the project single-threaded; a
	larger thread pool makes the project apartment-threaded.
	
	NOTE: When you change the threading model for an existing project, an error
	occurs if the project uses single-threaded ActiveX controls. Visual Basic
	prevents the use of single-threaded controls in apartment-threaded projects, as
	described in Converting Existing Projects.
	
	NOTE: When you specify Thread per Object (or a thread pool greater than one) for
	an ActiveX Exe project, only externally-created objects are created on new
	threads. (See "Designing Multithreaded Out-of-Process Components" in Books
	Online.) Thread per Object and Thread Pool are not available for ActiveX DLL and
	ActiveX Control projects, because thread creation is controlled by the client
	application.
	
	IMPORTANT: For Professional and Enterprise Edition users, the consequences of
	selecting Thread per Object or Thread Pool are discussed in detail in "Designing
	Multithreaded Out-of-Process Components" in Books Online.
	
	Visual Basic 5.0 Service Pack 2 and Unattended Execution
	--------------------------------------------------------
	
	Visual Basic 5.0 Service Pack 2 does not change the functioning of the Unattended
	Execution option. Unattended Execution still allows you to create components
	that can run without operator intervention on network servers. The only change
	made by Visual Basic 5.0 Service Pack 2 is that selecting Unattended Execution
	doesn't affect the threading model of your component.
	
	Limitations of the Apartment-Model Threading Feature
	----------------------------------------------------
	
	The following limitations apply to all editions of Visual Basic:
	
	- The development environment doesn't support multithreaded debugging. If you
	  have Microsoft Visual Studio, you can debug an apartment-threaded component
	  with the Visual Studio debugger after compiling it to native code with debug
	  information. You will also need a multithreaded client; MDI parent and child
	  forms must share data in ways that are difficult to make thread-safe.
	  Therefore, MDI forms are not allowed in apartment- threaded projects. On the
	  Project menu, "Add MDIForm" is grayed out in apartment-threaded ActiveX DLL
	  projects and in ActiveX Exe projects with Thread per Object selected (or with
	  a thread pool larger than one). If you change the threading model to
	  Apartment Threaded in a project that contains MDI forms, an error occurs.
	
	- Single-threaded ActiveX controls can cause numerous problems in multi-
	  threaded clients, in addition to performing poorly. Therefore, Visual Basic
	  prevents the use of single-threaded controls in projects where Threading
	  Model has been set to Apartment Threaded. For details, see Converting
	  Existing Projects.
	
	- Friend properties and methods can only be called by objects on the same
	  thread. Because they are not part of an object's public interface, they
	  cannot be marshaled between threads.
	
	- ActiveX Documents in ActiveX Exe projects will not be apartment-model
	  thread-safe unless you select Thread per Object or Thread Pool with a pool
	  size greater than one.
	
	- When a thread shows a form with vbModal, the form will be modal only to code
	  and forms on that thread. Code running in other threads will not be blocked
	  and forms shown by other threads will remain active.
	
	- Drag-and-drop between forms and controls will work only if the drag source
	  and the drag target are on the same thread. (OLE drag-and-drop, however, will
	  work universally.)
	
	- DDE between forms will work only if the forms are on the same thread.
	
	Converting Existing Projects
	----------------------------
	
	Once you have applied Visual Basic 5.0 Service Pack 2, you can add
	apartment-threading to your existing projects by changing the Threading Model
	option, as described in Selecting a Threading Model for Your Project, and
	recompiling the project. For many projects, this is all you need to do.
	
	If an existing ActiveX DLL, ActiveX EXE, or ActiveX control project uses
	single-threaded constituent controls, attempting to change Threading Model to
	Apartment Threaded will cause an error. Because of the number and severity of
	problems that single-threaded ActiveX controls cause for multithreaded clients,
	Visual Basic does not permit them to be used in ActiveX component projects. If
	you have an existing project that employs a single-threaded control, contact the
	vendor to see whether an apartment- threaded version is available.
	
	Forcing the Use of Single-Threaded Controls
	-------------------------------------------
	
	It is possible to trick Visual Basic into using a single-threaded control in an
	apartment-threaded project by manually editing the .vbp file. NOTE: Do not do
	this. The problems that single-threaded ActiveX controls can cause include:
	
	- If users tab to a single-threaded control on a form that is running on a
	  different thread, they will not be able to tab off the control. This occurs
	  because the single-threaded control's thread has no context for the focus on
	  the form's thread. The only way for the user to change the focus in this
	  situation is to use the mouse. Using a single-threaded control as a
	  constituent of an apartment-threaded control causes similar problems.
	
	- In a multithreaded application, activating a form by clicking on a
	  single-threaded control will fail if the form is on a different thread. This
	  also occurs when clicking on a single-threaded constituent of an
	  apartment-threaded control.
	
	- Using a single-threaded OCX in a multithreaded application causes performance
	  problems because all of the controls the OCX provides must run on the same
	  thread. For controls on forms running in different threads, all communication
	  requires expensive cross-thread calls. An apartment-threaded ActiveX control
	  that uses single-threaded constituent controls will cause similar performance
	  problems.
	
	- In a multithreaded application, the TAB key and access keys (for example,
	  ALT+A) will not work for single-threaded controls that are not on the
	  application's main thread. An apartment-threaded ActiveX control that uses
	  single-threaded constituent controls will experience similar problems.
	
	- If your apartment-threaded control sets the Picture property of a single-
	  threaded constituent control (or any other property that takes a Picture
	  object), errors will occur in multi-threading clients because the Picture
	  object cannot be marshaled between threads.
	
	IMPORTANT: Single-threaded controls can cause these and other problems in any
	multithreaded component or application you build, using Visual Basic or any
	other development tool.
	
	Design Considerations for ActiveX DLL and ActiveX Control Projects
	------------------------------------------------------------------
	
	Objects provided by in-process components are created on client threads; your DLL
	or OCX cannot create threads of its own. The first time a client thread creates
	an instance of an object provided by your component, a new apartment will be
	created for that thread and your Sub Main will execute for the new apartment.
	All of the objects your component provides for that client thread will reside in
	the same apartment.
	
	If you have designed your component so that all the instances of a class share
	some common global data, that data will now be shared only by objects that
	happen to be on the same thread. If you have global code that accesses a
	database, that access will now occur separately on each thread.
	
	For example, suppose that a multithreaded client shows one instance of your
	Widget control on a form on thread A and two more instances on a form on thread
	B. The control instances will be in two apartments, each with a copy of your
	global variables. Sub Main will execute once for each apartment. The two
	controls on thread B will share global state, separate from the global state of
	the control on thread A.
	
	Other design considerations are discussed in Changes to "Apartment-Model
	Threading in Visual Basic" and Changes to "Designing Thread-Safe DLLs" in this
	article, and in the corresponding topics in Visual Basic 5.0 Books Online.
	
	Design Considerations for ActiveX EXE Projects
	----------------------------------------------
	
	The most important difference between single-threaded and apartment- threaded
	out-of-process components is that all global data (including the properties of
	the App object) is replicated for each thread. One of the implications of this
	is that Sub Main will be run every time a new thread is created.
	
	Other design considerations for out-of-process components are discussed in
	Changes to "Apartment-Model Threading in Visual Basic" and Changes to "Designing
	Multithreaded Out-of-Process Components" in this document, and in the
	corresponding topics in Visual Basic 5.0 Books Online.
	
	Changes to the Visual Basic 5.0 Documentation
	---------------------------------------------
	
	The following topics describe specific changes to the indicated topics in Visual
	Basic 5.0 Books Online:
	
	Changes to: "Apartment-Model Threading in Visual Basic"
	
	Changes to: "Designing Thread-Safe DLLs"
	
	Changes to: "Designing Multithreaded Out-of-Process Components"
	
	If you have the Professional or Enterprise Edition of Visual Basic, you can
	locate these topics in Books Online using the Contents pane:
	
	Component Tools Guide
	
	   Creating ActiveX Components
	       Building Code Components
	         Scalability and Multithreading
	
	NOTE: The Books Online browser is not included in the Control Creation Edition.
	The topics listed above are not included in the Visual Basic 5.0 documentation
	parts that can be downloaded for use with the Control Creation Edition. However,
	the material on reentrancy and designing thread- safe DLLs contained in the
	following two topics will be of interest to Control Creation Edition users.
	
	Changes to "Apartment-Model Threading in Visual Basic"
	------------------------------------------------------
	
	The original topic in Books Online explains that Visual Basic maintains a
	separate copy of global data for each thread. A side effect of this, which is
	not mentioned in Books Online, is that Sub Main is executed for each new
	apartment (that is, for each new thread). Otherwise, there would be no way to
	initialize global data for the thread. This is discussed further in Changes to
	"Designing Thread-Safe DLLs" and Changes to "Designing Multithreaded
	Out-of-Process Components" below.
	
	Where You Can Use Threading
	---------------------------
	
	It is no longer true that components must be marked for Unattended Execution in
	order to use apartment-threading. Unattended Execution is now a separate option
	on the General tab of the Project Properties dialog box, as described in
	Selecting a Threading Model for Your Project, above.
	
	Reentrancy
	----------
	
	The original topic states that when you make a cross-thread call, the method
	you're calling is protected from being reentered as long as the method does not
	yield (for example, by calling DoEvents). It is important to note that a method
	can also yield by making a cross-thread or cross- process method call of its own
	or by showing a form.
	
	Changes to "Designing Thread-Safe DLLs"
	---------------------------------------
	
	The Books Online topic now applies to ActiveX Control projects, as well as
	ActiveX DLL projects.
	
	The procedure for making an ActiveX DLL project apartment-threaded has change, as
	described in Selecting a Threading Model for Your Project (above). It is no
	longer necessary to suppress all user interaction (the Unattended Execution
	option) in order to have an apartment-threaded DLL.
	
	When you create an instance of a form at run-time, Visual Basic follows the same
	rules it uses for other private objects. That is, the new form is created on the
	thread where the New operator is executed. If you create a form implicitly (for
	example, by accessing a form property using a variable that was declared As New
	Form1), the form is created on the thread where the code was executed.
	
	NOTE: A special case of implicit form creation is the pre-declared ID (for
	example, Form1), a hidden global form variable that Visual Basic maintains for
	every form class. Because Visual Basic duplicates global data for each
	apartment, there is a separate Form1 for every thread. To avoid confusion, you
	may find it helpful to avoid using pre-declared IDs in apartment- threaded
	components by explicitly declaring your own form variables.
	
	NOTE: Duplicate global data means that a variable you declare Public in a
	standard module is global only to the thread; each thread has an instance of the
	variable. It also means that the properties of the App object, such as
	App.ThreadID, have separate instances for each thread.
	
	Unlike forms, ActiveX controls are public objects that can be created and used by
	client forms. An instance of an ActiveX control always resides on the same
	thread as the client form that uses it.
	
	IMPORTANT: In an apartment-model DLL, a new apartment is created for each client
	thread that requests objects that the DLL provides. The first time a client
	thread requests such an object, Sub Main executes for the new apartment. A DLL
	cannot create threads of its own.
	
	Changes to "Designing Multithreaded Out-of-Process Components"
	--------------------------------------------------------------
	
	It is no longer necessary to suppress all user interaction (the Unattended
	Execution option) in order to have a multithreaded Exe. The descriptions of
	Thread per Object and Thread Pool (round-robin threading) remain the same.
	
	You can make an ActiveX Exe project apartment-threaded by opening the General tab
	of the Project Properties dialog box and selecting Thread per Object or
	selecting Thread Pool and setting a pool size greater than one.
	
	Like other private objects, forms reside on the thread where they were created.
	Private objects cannot be created with the CreateObject function, so they cannot
	be used to start new threads.
	
	IMPORTANT: In a multithreaded executable, Sub Main executes independently for
	each new thread. Visual Basic provides no way to determine which thread was
	created first.
	
	Apartment-Threaded Controls for Internet Explorer 4.0
	-----------------------------------------------------
	
	Internet Explorer 4.0 displays windows using multiple threads of execution. When
	two different windows in Internet Explorer 4.0 display instances of the same
	ActiveX control, the OCX must provide an instance to each thread. If both
	instances are provided from the same apartment in the OCX (as is the case with
	Visual Basic 5.0), one of the control instances will suffer from degraded
	performance because of cross-thread marshaling.
	
	In addition to poor performance, a single-threaded control can cause problems
	with focus, tabbing, and accelerator keys when used in a multithreaded
	application.
	
	Compiling your OCX with Visual Basic 5.0 Service Pack 2 improves performance and
	removes these problems. Each control instance used by Internet Explorer 4.0 runs
	on the same thread as the window that displays the control, because the OCX can
	support a separate apartment for each client thread.
	
	Most ActiveX Controls Shipped with Visual Basic Have Been Updated
	-----------------------------------------------------------------
	
	Visual Basic 5.0 Service Pack 2 includes new versions of most of the ActiveX
	controls that shipped with Visual Basic 5.0. The updated controls are now
	apartment-model threaded and will perform equally well on single- threaded or
	multithreaded clients. Controls that are still single-threaded include DBGrid,
	MSChart, and the legacy controls that were shipped in the Tools directory for
	Visual Basic 5.0.
	
	ActiveX Controls Authored with Visual Basic
	-------------------------------------------
	
	Once you have applied Visual Basic 5.0 Service Pack 2, new ActiveX control
	projects will default to apartment-model threading. You can add apartment-
	threading to an existing ActiveX Control project by changing the threading
	model, as described in Selecting a Threading Model for Your Project, and
	recompiling the project. For many ActiveX control projects, this is all you need
	to do.
	
	If your ActiveX control project uses single-threaded constituent controls,
	attempting to change Threading Model to Apartment Threaded will cause an error.
	Because of the number and severity of problems that single-threaded ActiveX
	controls cause for multithreaded clients, Visual Basic does not permit them to
	be used as constituents of apartment-threaded ActiveX controls. This is
	discussed in Converting Existing Projects.
	
	If you have existing ActiveX controls that employ single-threaded constituent
	controls, contact the vendor of the single-threaded control to see whether an
	apartment-threaded version is available.
	
	Other design considerations for apartment-threaded ActiveX Controls are discussed
	in Converting Existing Projects.
	
	Creating a Thread-Safe DLL with Forms
	-------------------------------------
	
	You can now set the Threading Model option to Apartment-Threaded in ActiveX DLL
	projects that contain forms.
	
	Apartment-threaded DLLs cannot create their own threads; the first time a client
	thread requests an object provided by your DLL, a new apartment is created, and
	Sub Main executes for that apartment. All public objects requested by that
	client will reside in the same apartment, and will share global data. Any
	private objects (including forms) that are created by the public objects will
	also reside in the apartment.
	
	Visual Basic does not provide any way for apartments to become aware of each
	other. However, a multithreaded client could obtain a reference to an object on
	Thread A, and pass that reference to an object on Thread B. If your DLL allows
	this, you should read the information on reentrancy in "Apartment Model
	Threading in Visual Basic" in Books Online, and in Changes to "Apartment-Model
	Threading in Visual Basic" in this document.
	
	IMPORTANT: Modal forms shown by a thread do not block execution of code on other
	threads and are not modal to forms on other threads. Showing a form yields
	control, just as calling DoEvents would, and, therefore, may cause the code in
	an object to be re-entered.
	
	Creating a Multithreaded Test Application
	-----------------------------------------
	
	Applying Visual Basic 5.0 Service Pack 2 to the Professional and Enterprise
	Editions of Visual Basic allows you to create multithreaded test applications to
	exercise your multithreaded controls. The steps to create a simple multithreaded
	application are as follows:
	
	1. Open a new ActiveX EXE project, and name the default class module MainApp.
	  Set the Instancing property for MainApp to PublicNotCreatable. A MainApp
	  object will occupy the application's first thread, and display the main user
	  interface.
	
	2. On the General tab of the Project Properties dialog box, select Sub Main in
	  the Startup Object box, select Thread per Object in the Threading Model box,
	  and enter a unique value for the Project name. (Project Name determines the
	  type library name; problems may arise if two applications have the same type
	  library name.) "ThreadDemo" is the project name used in the example below. On
	  the Component tab, select Standalone in the Start Mode box.
	
	3. Add a form, name it frmProcess, and set the Visible and ControlBox properties
	  to False. This form functions as a hidden window which Sub Main will use to
	  identify the main thread for the process. No code is needed for this form.
	
	4. Add a standard module to the project. In this module, place the declarations,
	  the Sub Main procedure, and the EnumThreadWndMain procedure shown below. As
	  explained in the accompanying text and code comments, Sub Main will execute
	  when your application starts and every time you create a new thread. The Sub
	  Main sample code demonstrates how to identify the first thread, so that you
	  know when to create MainApp.
	
	5. Add a form and name it frmMTMain. This form provides the main user interface
	  for the test application. Add to it the single declaration and the
	  Form_Unload event immediately above the heading "Multiple Instances of the
	  Test Application."
	
	6. In the Class_Initialize event procedure for MainApp, add code to show
	  frmMTMain. Code to do this is provided below.
	
	7. To create additional test threads, you must have at least one class in your
	  project whose Instancing property is set to MultiUse. Add a class module and
	  form, and then insert the code provided under the heading "Creating New
	  Threads." Because you selected Thread per Object for this project, every
	  public object that is externally created will start on a new thread. This
	  means that you can create a new thread by using the CreateObject function to
	  create an instance of your MultiUse class from its programmatic ID (ProgID),
	  as discussed in the accompanying text.
	
	8. Add code to frmMTMain to create new threads by creating instances of the
	  MultiUse classes you defined. In the example below, see the code under the
	  heading "Creating New Threads."
	
	9. The development environment does not support multi-threading. If you press
	  the F5 key to run the project, all objects will be created on the same
	  thread. In order to test multithreaded behavior, you must compile the ActiveX
	  EXE project and run the resulting executable.
	
	  IMPORTANT: To ensure that each new MultiUse object starts a new thread, you
	  must use Thread per Object rather than Thread Pool.
	
	Determining the Main Thread During Sub Main
	-------------------------------------------
	
	Sub Main executes for every new thread because Visual Basic maintains a separate
	copy of your global data for each thread (each apartment). In order to
	initialize global data for the thread, Sub Main must execute. If your Sub Main
	loads a hidden form or displays your application's main user interface, new
	copies of those forms will be loaded for every new thread you create.
	
	The following code determines whether Sub Main is executing in the first thread
	so that you can load the hidden form only once and display the test
	application's main user interface only once:
	
	     ' Root value for hidden window caption
	     Public Const PROC_CAPTION = "ApartmentDemoProcessWindow"
	
	     Public Const ERR_InternalStartup = &H600
	     Public Const ERR_NoAutomation = &H601
	
	     Public Const ENUM_STOP = 0
	     Public Const ENUM_CONTINUE = 1
	
	     Declare Function FindWindow Lib "user32" Alias "FindWindowA" _
	     (ByVal lpClassName As String, ByVal lpWindowName As String) _
	      As Long
	
	     Declare Function GetWindowThreadProcessId Lib "user32" _
	     (ByVal hwnd As Long, lpdwProcessId As Long) As Long
	
	     Declare Function EnumThreadWindows Lib "user32" _
	     (ByVal dwThreadId As Long, ByVal lpfn As Long, _
	      ByVal lParam As Long) As Long
	
	     ' Window handle retrieved by EnumThreadWindows.
	     Private mhwndVB As Long
	     ' Hidden form used to identify main thread.
	     Private mfrmProcess As New frmProcess
	     ' Process ID.
	     Private mlngProcessID As Long
	
	     Sub Main()
	         Dim ma As MainApp
	
	         ' Borrow a window handle to use to obtain the process
	         '   ID (see EnumThreadWndMain call-back, below).
	         Call EnumThreadWindows(App.ThreadID, AddressOf _
	             EnumThreadWndMain, 0&)
	         If mhwndVB = 0 Then
	             Err.Raise ERR_InternalStartup + vbObjectError, _
	                 , "Internal error starting thread"
	         Else
	             Call GetWindowThreadProcessId(mhwndVB, mlngProcessID)
	             ' The process ID makes the hidden window caption unique.
	             If 0 = FindWindow(vbNullString, _
	                            PROC_CAPTION & CStr(mlngProcessID)) Then
	                 ' The window wasn't found, so this is the first thread.
	                 If App.StartMode = vbSModeStandalone Then
	                     ' Create hidden form with unique caption.
	                     mfrmProcess.Caption = PROC_CAPTION & CStr(mlngProcessID)
	                     ' The Initialize event of MainApp (Instancing =
	                     '   PublicNotCreatable) shows the main user interface.
	                     Set ma = New MainApp
	                     ' (Application shutdown is simpler if there is no
	                     '   global reference to MainApp; instead, MainApp
	                     '   should pass Me to the main user form, so that
	                     '   the form keeps MainApp from terminating.)
	                 Else
	                     Err.Raise ERR_NoAutomation + vbObjectError, , _
	                         "Application can't be started with Automation"
	                 End If
	             End If
	         End If
	     End Sub
	
	     ' Call-back function used by EnumThreadWindows.
	     Public Function EnumThreadWndMain _
	         (ByVal hwnd As Long, ByVal lParam As Long) As Long
	         ' Save the window handle.
	         mhwndVB = hwnd
	         ' The first window is the only one required.
	         ' Stop the iteration as soon as a window has been found.
	         EnumThreadWndMain = ENUM_STOP
	     End Function
	
	     ' MainApp calls this Sub in its Terminate event;
	     '   otherwise the hidden form will keep the
	     '   application from closing.
	     Public Sub FreeProcessWindow()
	         Unload mfrmProcess
	         Set mfrmProcess = Nothing
	     End Sub
	
	IMPORTANT: This technique for identifying the first thread may not work in future
	versions of Visual Basic.
	
	Note that Sub Main takes no action for any thread after the first. When you add
	code that creates MultiUse objects (in order to start subsequent threads), be
	sure to include code to initialize those objects.
	
	EnumThreadWindows is used with a call-back, EnumThreadWndMain, to locate one of
	the hidden windows Visual Basic creates for its internal use. The window handle
	of this hidden window is passed to GetWindowThreadProcessId, which returns the
	process ID. The process ID is then used to create a unique caption for the
	hidden window (frmProcess) that Sub Main loads. Subsequent threads detect this
	window and, thus, can tell that they don't need to create the MainApp object.
	These gyrations are necessary because Visual Basic does not provide a way to
	identify the application's main thread.
	
	The MainApp class, in its Initialize event, displays the test application's main
	form. MainApp should pass its Me reference to the main form, so that the form
	keeps MainApp from terminating. From the main user interface, you can create all
	subsequent threads. Setting the Instancing property for MainApp to
	PublicNotCreatable helps you avoid displaying two main user interface forms.
	
	A simple example of a MainApp class and its associated form (steps 5 and 6,
	above) might look like this:
	
	     ' Code for a MainApp class.
	     Private mfrmMTMain As New frmMTMain
	
	     Private Sub Class_Initialize()
	         Set mfrmMTMain.MainApp = Me
	         mfrmMTMain.Caption = _
	               mfrmMTMain.Caption & " (" & App.ThreadID & ")"
	         mfrmMTMain.Show
	        End Sub
	
	     Friend Sub Closing()
	         Set mfrmMTMain = Nothing
	
	     End Sub
	
	     Private Sub Class_Terminate()
	         ' Clean up the hidden window.
	         Call FreeProcessWindow
	     End Sub
	
	     ' Code for the form frmMTMain.
	     Public MainApp As MainApp
	
	     Private Sub Form_Unload(Cancel As Integer)
	         Call MainApp.Closing
	         Set MainApp = Nothing
	     End Sub
	
	Multiple Instances of the Test Application
	------------------------------------------
	
	Including the process ID in the hidden window caption allows multiple instances
	of the test application to run without interfering with one another.
	
	When you call CreateObject, the instance of the public class you create will be
	on a thread in the current application instance. This is because CreateObject
	always attempts to create an object in the current application before looking
	for other running Exe components that might supply the object.
	
	Useful Properties for the Apartment
	-----------------------------------
	
	You may find it useful to expose the process ID as a read-only property of the
	module that contains Sub Main:
	
	     'This code not required for the test application
	     Public Property Get ProcessID() As Long
	         ProcessID = mlngProcessID
	     End Property
	
	This allows any object on the thread to get the process ID by calling the
	unqualified ProcessID property. You may also find it useful to expose a Boolean
	IsMainThread property in this fashion.
	
	Creating New Threads
	--------------------
	
	The Thread per Object option causes every public object that is externally
	created (created using the CreateObject function) to start on a new thread. To
	create a new thread, simply use the programmatic ID (ProgID) of one of your
	MultiUse classes:
	
	     'This code not included in the test application
	     Dim tw As ThreadedWindow
	     Set tw = CreateObject("ThreadDemo.ThreadedWindow")
	
	The variable "tw" now contains a reference to an object on a new thread. All
	calls to the properties and methods of this object that are made using "tw" will
	be subject to the extra overhead of cross-thread marshaling.
	
	NOTE: An object created with the New operator is not created on a new thread. It
	resides on the same thread where the New operator was executed. See "Designing
	Multithreaded Out-of-Process Components" and "How Object Creation Works in
	Visual Basic Components" in Books Online.
	
	To ensure that MainApp doesn't terminate until all of the other threads are
	finished, you can give each public class a MainApp property. When an object
	creates a MultiUse object on a new thread, it can pass the new object a
	reference to the MainApp object as part of the initialization process. (You can
	also pass MainApp a reference to the new object, so that MainApp has a
	collection of references to all objects that control threads. However, remember
	that this will create circular references. See "Dealing with Circular
	References" in Books Online.)
	
	If you want a class that controls a thread to show a form, you should provide it
	with an Initialize method (not to be confused with the Initialize event) or a
	Show method that displays the form. Don't show the form in the Class_Initialize
	event procedure, as this could cause timing errors when you create instances of
	the class. In a very simple case, the code for a MultiUse ThreadedWindow class
	and its form, frmThreadedWindow, might look like this:
	
	     'Code for a MultiUse ThreadedWindow class.
	     Private mMainApp As MainApp
	     Private mfrm As New frmThreadedWindow
	
	     Public Sub Initialize(ByVal ma As MainApp)
	         Set mMainApp = ma
	         Set mfrm.ThreadedWindow = Me
	         mfrm.Caption = mfrm.Caption & " (" & App.ThreadID & ")"
	         mfrm.Show
	     End Sub
	
	     Friend Sub Closing()
	         Set mfrm = Nothing
	     End Sub
	
	     'Code for the form frmThreadedWindow.
	     Public ThreadedWindow As ThreadedWindow
	
	     Private Sub Form_Unload(Cancel As Integer)
	         Call ThreadedWindow.Closing
	         Set ThreadedWindow = Nothing
	     End Sub
	
	The following code snippet shows how you might initialize the ThreadedWindow
	object:
	
	     'Code for the test application's main form (frmMTMain).
	     Private Sub mnuFileNewTW_Click()
	         Dim tw As ThreadedWindow
	         Set tw = CreateObject("ThreadDemo.ThreadedWindow")
	         ' Tell the new object to show its form, and
	         '   pass it a reference to the main
	         '   application object.
	         Call tw.Initialize(Me.MainApp)
	     End Sub
	
	If you have a number of classes that can control threads, you can make your code
	more generic by defining an IApartment interface to contain the Initialize
	method. When you implement IApartment in each class, you can provide the
	appropriate Initialize method code for that class. Your thread creation code
	might look like this:
	
	     'This code not required for the test application
	     Private Sub mnuFileNewObject_Click(Index As Integer)
	         Dim iapt As IApartment
	         Select Case Index
	           Case otThreadedWindow
	             Set iapt = CreateObject("ThreadDemo.ThreadedWindow")
	           ' (other cases[ASCII 133])
	         End Select
	         ' Common code to initialize objects.
	         Call iapt.Initialize(MainApp)
	     End Sub
	
	NOTE: You can make an IXxxxApartment interface that's known only to the
	Multithreaded application by defining the interface in a separate type library.
	In the ActiveX Exe project, set a reference to the type library.
	
	Keeping References to Threaded Objects
	--------------------------------------
	
	To ensure proper shutdown of a multithreaded application, you must keep careful
	track of all references to the MultiUse objects you use to create and control
	threads.
	
	Define your object lifetime goals clearly. For example, consider the case of a
	MultiUse object that shows a form. The easiest way to manage object lifetime is
	to have the object pass the form a Me reference; the form then keeps the object
	alive. When the user closes the form, the form's Unload event must set all
	references to the MultiUse object to Nothing so that the object can terminate
	and, in turn, clean up its reference to the form. (You may find it useful to
	give the MultiUse object a Friend method that cleans up the reference to the
	form and all other internal object references; the form's Unload event can call
	this method.)
	
	If the object that controls a thread creates additional objects on the thread
	using the New operator, make sure you clean up references to those objects. The
	thread cannot close until all references to objects that were created on the
	thread have been released. Open threads consume system resources.
	
	Friend Methods Cannot Be Used Cross-Thread
	------------------------------------------
	
	Because Friend properties and methods are not part of the public interface of a
	class, you cannot call them from another thread. Cross-thread calls between
	objects are limited to properties and methods that are declared Public.
	
	Reentrancy
	----------
	
	If a method of an object yields by calling DoEvents, showing a modal form, or
	making a secondary call to an object on another thread, then the code in the
	method can be entered by a second caller before the first call completes. If
	such a method uses or changes property values or module-level variables, this
	could result in an invalid internal state for the object. To protect against
	reentrancy, you can:
	
	- Avoid yielding.
	
	- Keep a module-level Boolean flag for each method. When a method begins, it
	  tests this flag to determine whether a method call is in progress. If not,
	  the method sets the flag to True and continues; otherwise it raises an error.
	  You must be careful to turn this flag off when the method completes or exits
	  for any reason.
	
	- Write reentrant methods (methods that don't depend on module- level data).
	
	Asynchronous Tasks
	------------------
	
	Visual Basic doesn't provide a way to fork execution (to have one thread initiate
	a method call on a new thread and immediately resume processing on the original
	thread). You can simulate this behavior in your test application by having the
	original method call turn on a timer and then return immediately. When the timer
	event occurs, you can turn the timer off and perform the asynchronous
	processing. This technique is discussed in "Asynchronous Call-Backs and Events"
	in Books Online, and is demonstrated in Books Online (see "Creating an ActiveX
	Exe Component") and in the Coffee sample application.
	
	Using the Multithreaded Test Application
	----------------------------------------
	
	You must compile the multithreaded test application in order to test your
	apartment-threaded component because the Visual Basic development environment
	does not currently support multiple threads of execution. If you have Visual
	Studio, you may find it useful to compile the test application with debugging
	information for native code debugging so that you can use the Visual Studio
	debugger.
	
	Note on Safe Scripting for ActiveX Controls
	-------------------------------------------
	
	Two of the apartment-threaded controls included with Visual Basic 5.0 Service
	Pack 2, the Common Dialog control and the Toolbar control, now support the
	ActiveX IObjectSafety interface. When these controls are used in an environment
	where safe scripting is in force, such as Internet Explorer, they will be marked
	Safe for Scripting. However, certain features of these controls will be disabled
	in order to qualify them as safe for scripting:
	
	- The Toolbar control cannot save its state to the registry because an
	  ill-behaved script could exploit this to write uncontrolled information to
	  the registry.
	
	- Show Help is disabled for the Common Dialog control because an ill- behaved
	  script could use this feature to execute Help macros that might cause harm to
	  a user's computer.
	
	Packing List
	------------
	
	The following files are included in Visual Basic 5.0 Service Pack 2:
	
	asycfilt.dll
	c2.exe
	comct232.dep
	comct232.ocx
	comctl32.dep
	comctl32.ocx
	comdlg32.dep
	comdlg32.ocx
	dbgrid32.dep
	dbgrid32.ocx
	dblist32.dep
	dblist32.ocx
	mci32.dep
	mci32.ocx
	mscdrun.dep
	mscdrun.dll
	mscomm32.dep
	mscomm32.ocx
	mscondes.dll
	msflxgrd.dep
	msflxgrd.ocx
	msinet.ocx
	msinet.dep
	msmapi32.dep
	msmapi32.ocx
	msmask32.dep
	msmask32.ocx
	msrdc20.dep
	msrdc20.ocx
	msrdo20.dep
	msrdo20.dll
	msstkprp.dll
	msvbvm50.dll
	mswinsck.dep
	mswinsck.ocx
	oleaut32.dll
	olepro32.dll
	picclp32.dep
	picclp32.ocx
	readme.wri
	richtx32.dep
	richtx32.ocx
	setup1.bas
	setup1.exe
	setupwiz.exe
	stdole2.tlb
	sysinfo.dep
	sysinfo.ocx
	tabctl32.dep
	tabctl32.ocx
	vb5.exe
	vb5dep.ini
	vb5ide.dll
	vb5sp2.htm
	vb5sp2.wri
	vba332me.dll
	vba5.dll
	
	Alpha systems only:
	
	adme.dll
	dtccm.dll
	dtctrace.dll
	dtcutil.dll
	msdtcprx.dll
	
	REFERENCES
	==========
	
	Search for VB5FixListSP2 on the Knowledge Base Web site at:
	http://msdn.microsoft.com/support
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp500 kbVS97sp2fix kbvbp500sp2fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB500
	Version           : WINDOWS:5.0,97sp2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
