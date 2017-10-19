---
layout: page
title: "Q194873: HOWTO: Access a Visual Basic ActiveX DLL from Visual C++"
permalink: kb/194/Q194873/
---

## Q194873: HOWTO: Access a Visual Basic ActiveX DLL from Visual C++

	Article: Q194873
	Product(s): Microsoft C Compiler
	Version(s): winnt:5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbActiveX kbVC600 kbCodeSam
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows three ways to access a Visual Basic ActiveX DLL from a Visual
	C++ 6.0 executable.
	
	MORE INFORMATION
	================
	
	This article represents an introduction to creating Visual C++ clients for
	Visual Basic ActiveX components. If you are already proficient with Visual C++,
	you may wish to refer to the reference section for a list of more advanced
	topics.
	
	Steps to Create the Visual Basic Server
	---------------------------------------
	
	1. Create a Visual Basic ActiveX DLL project. Class1 is created by default.
	
	2. Add the following code to Class1:
	
	        Public Function MyVBFunction(x As Integer) As Integer
	           MsgBox x
	        End Function
	
	3. Compile the DLL as c:\Project1.dll and exit Visual Basic.
	
	Method 1 - CreateDispatch:
	
	1. Start Visual C++ and select New on the File menu. Choose MFC AppWizard (Exe)
	  and a project name, and Click OK. When the MFC AppWizard dialog box appears,
	  click Finish. Click OK on the next dialog box.
	
	2. Select ClassWizard on the View menu, pick Ctst1App in the Class Name box, and
	  double-click InitInstance in the Messages box. Click Edit Code to bring up
	  the code for BOOL CTst1App::InitInstance(), find the line
	  AfxEnableControlContainer();, and add the following line before it:
	
	        AfxOleInit();
	
	3. Select ClassWizard from the View menu and click the Automation tab. Click
	  AddClass and select "from a TypeLibrary". Specify Project1.dll, the Visual
	  Basic DLL which was created in step 3. When the Confirm Classes dialog box
	  appears, click OK. Click OK again to close the MFC ClassWizard dialog box.
	
	4. Open your <App Name>.cpp file and add the line #include "Project1.h".
	  You need to include Project1.h wherever you have code that accesses
	  project1.dll.
	
	5. Open the ClassWizard again. On the Message Maps tab, select CAboutDlg in the
	  Class Name box and IDOK in the Object IDs box, and then double-click
	  BN_CLICKED. Click OK in response to the dialog box and OK again to close the
	  ClassWizard.
	
	6. Open <App Name>.cpp, scroll to the bottom to theCAboutDlg::OnOK(), and
	  replace it with the following code:
	
	        void CAboutDlg::OnOK()
	        {
	
	        short st = 2;
	        short st1;
	        _Class1 p;
	        p.CreateDispatch("Project1.Class1");
	        st1 = p.MyVBFunction(&st);
	        CDialog::OnOK();
	        }
	
	7. Compile your .exe file (F7).
	
	8. Run the .exe file and select About on the Help menu. Click OK on the About
	  box and the message box that was specified in project1.dll appears. Click the
	  Close button to dismiss the dialog box.
	
	Method 2 - #IMPORT:
	
	1. Start Visual C++ 6.0 and create a Win32 Console Application. Select "An Empty
	  Project" and click Finish.
	
	2. Point to Add to Project on the Project menu and click New to add a new C++
	  source file to the project. Paste the following code in the new source file
	  and save it:
	
	        #include <stdio.h>
	
	        // This is the path for your DLL.
	        // Make sure that you specify the exact path.
	
	        #import "c:\project1.dll"  no_namespace
	
	        void main()
	        {
	         BSTR bstrDesc;
	
	        try
	        {
	        CoInitialize(NULL);
	        short st = 2;
	         short st1;
	        // Declare the Interface Pointer for your Visual Basic object. Here,
	        // _Class1Ptr is the Smart pointer wrapper class representing the
	        // default interface of the Visual Basic object.
	
	        _Class1Ptr ptr;
	        // Create an instance of your Visual Basic object, here
	        // __uuidof(Class1) gets the CLSID of your Visual Basic object.
	
	         ptr.CreateInstance(__uuidof(Class1));
	         st1 = ptr->MyVBFunction(&st);
	        }
	        catch(_com_error &e)
	        {
	         bstrDesc = e.Description();
	
	        }
	        CoUninitialize();
	        }
	
	3. Compile and run your project. The message box from Project1.DLL should
	  appear.
	
	The #import method can be used in a Win32 Application, a Console Application, or
	in MFC as well.
	
	Method 3 - Pure COM Interface
	
	1. Start Visual C++ and select New from the File menu. Choose MFC AppWizard
	  (Exe), name the project tst1, and click OK. When the MFC Appwizard dialog box
	  appears, select Dialog Based and click Finish. Click OK when the next dialog
	  box appears.
	
	2. The Resource Editor is started by default. Delete all the controls on the
	  dialog box and add a Command button on it, retaining the default caption
	  "Button1".
	
	3. Double-click Button1 to display the Add Member Function dialog box. Click OK
	  to accept the name OnButton1.
	
	4. Click OLE/COM Object Viewer on the Tools menu. Select View Typelib from the
	  File menu and choose the Project1.dll you created earlier. Click Open to
	  display the ITypeLib Viewer, which contains the .idl file for your DLL.
	
	5. Copy the contents of your .idl file (contents of the right pane) to the
	  Clipboard. Hold the SHIFT key down while paging or scrolling from the first
	  character to the end of the text in the pane. Press Ctrl+C to copy the marked
	  text to the Clipboard.
	
	6. Click New on Visual C++ File menu. Select Text File on the New dialog box,
	  name the file test1.idl, and click OK.
	
	7. A blank text file appears. Paste the data from the Clipboard into it and save
	  the file.
	
	8. Select Settings from the Project menu, expand the tst1 and Source Files nodes
	  of the tree view, and select test1.idl. Click the MIDL tab, enter test1.h in
	  the "Output header file name" box, and click OK.
	
	9. Open tst1Dlg.cpp and add the following files to the includes section:
	
	        #include <initguid.h>
	        #include "test1.h"
	
	10. Click the ClassWizard on the View menu, select Ctst1App in the Class Name
	  box, and double-click InitInstance in the Messages box. Click Edit Code to
	  bring up the code for:
	
	        BOOL CTst1App::InitInstance()
	
	  Find the line:
	
	        AfxEnableControlContainer();
	
	  Add the following line before it:
	
	        AfxOleInit();
	
	11. Open the ClassWizard again. On the Message Maps tab select CTst1Dlg in the
	  Class Name box and IDC_BUTTON1 in the Object IDs box. Double-click
	  BN_CLICKED in the Messages box, and click Edit Code to bring up the code for
	  void CTst1Dlg::OnButton1(). Replace the OnButton1() function with the
	  following code:
	
	        void CTst1Dlg::OnButton1()
	        {
	           // TODO: Add your control notification handler code here.
	
	           _Class1 *pClass = NULL;
	           IUnknown *pUnk = NULL;
	
	        //   HRESULT hr = CoCreateInstance(CLSID_Class1,NULL,
	        //   CLSCTX_INPROC_SERVER,IID__Class1,(void **)&pClass);
	        //   You can directly get the Interface ID as in the previous line or
	        //   you can do a QueryInterface on IUnknown to get the IID
	        //   as in the following three lines:
	
	        HRESULT hr = CoCreateInstance(CLSID_Class1,NULL,CLSCTX_INPROC_SERVER,
	        IID_IUnknown,(void **)&pUnk);
	        hr = pUnk->QueryInterface(IID__Class1,(void **)&pClass);
	        pUnk->Release();
	
	        // Once you have the IID, you can make use of the interface pointer
	        // to access our Visual Basic DLL.
	
	        short st = 2;
	        short st1;
	        hr = pClass->MyVBFunction(&st,&st1);
	        pClass->Release();
	
	        }
	
	12. Compile your .exe file (F7) and run your application (F5). Click Button1 in
	  the dialog box. The message box from the Visual Basic DLL appears.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q178749 HOWTO: Create an Automation Project Using MFC and a Type Library
	
	  Q188817 HOWTO: VC++ MFC Client for the ComCallingJava Sample
	
	  Q186427 HOWTO: Catch Microsoft Excel 97 Application Events Using VC++
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbActiveX kbVC600 kbCodeSam 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : winnt:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	