---
title: "逐步解說：建立 Windows 傳統型應用程式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Windows 應用程式 [C++], Win32"
  - "WinMain"
  - "Win32 應用程式 [C++]"
  - "Windows 應用程式開發介面 [C++]"
ms.assetid: a247a9af-aff1-4899-9577-5f8104a0afbb
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：建立 Windows 傳統型應用程式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本逐步解說示範如何建立將在 視窗中顯示 "Hello, World\!" 的基本 Windows 傳統型應用程式。 您可以使用在這個逐步解說中開發的程式碼作為模式，來建立其他 Windows 傳統型應用程式。  
  
 Win32 API \(又稱為 Windows API\) 是建立 Windows 應用程式的 C 架構。 如需 Win32 API 的詳細資訊，請參閱 [Windows API](https://msdn.microsoft.com/en-us/library/cc433218.aspx)。  
  
> [!IMPORTANT]
>  為了更清楚地說明本文各步驟中的特定程式碼區段，我們可能會省略應用程式運作所需的一些程式碼陳述式，例如 Include 指示詞和全域變數宣告。 本文結尾的＜範例＞一節將顯示完整程式碼。  
  
## 必要條件  
 若要完成此逐步解說，您必須了解 C\+\+ 語言的基礎。  
  
 如需影片示範，請參閱 Visual Studio 2008 文件中的[作法影片：建立 Win32 應用程式 \(C\+\+\)](http://go.microsoft.com/fwlink/?LinkId=102471)。  
  
### 建立 Win32 專案  
  
1.  在 \[檔案\] 功能表上，按一下 \[新增\] 及 \[專案\]。  
  
2.  在 \[新增專案\] 對話方塊的左窗格中，依序按一下 \[已安裝的範本\] 和 \[Visual C\+\+\]，然後選取 \[Win32\]。 在中間窗格選取 \[Win32 專案\]。  
  
     在 \[名稱\] 方塊中，輸入專案的名稱，例如 `win32app`。 按一下 \[**確定**\]。  
  
3.  在 \[Win32 應用程式精靈\] 的 \[歡迎使用\] 頁面上，按一下 \[下一步\]。  
  
4.  在 \[應用程式設定\] 頁面的 \[應用程式類型\] 下，選取 \[Windows 應用程式\]。 在 \[其他選項\] 下，選取 \[空專案\]。 按一下 \[完成\] 建立專案。  
  
5.  以滑鼠右鍵按一下**方案總管**中的 Win32app 專案，按一下 \[加入\]，然後按一下 \[新增項目\]。 在 \[加入新項目\] 對話方塊中，選取 \[C\+\+ 檔 \(.cpp\)\]。 在 \[名稱\] 方塊中，輸入檔案的名稱，例如 `GT_HelloWorldWin32.cpp`。 按一下 \[加入\]。  
  
### 啟動 Windows 傳統型應用程式  
  
1.  就像每個 C 應用程式和 C\+\+ 應用程式都必須有 `main` 函式作為起點，每個 Win32 應用程式也都必須有 `WinMain` 函式。`WinMain` 具有下列語法。  
  
    ```  
    int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow);  
    ```  
  
     如需這個函式之參數和傳回值的相關資訊，請參閱 [WinMain 函式](http://msdn.microsoft.com/library/windows/desktop/ms633559)。  
  
2.  由於應用程式程式碼必須使用現有的定義，因此請將 Include 陳述式加入檔案中。  
  
    ```  
    #include <windows.h> #include <stdlib.h> #include <string.h> #include <tchar.h>  
    ```  
  
3.  除了 `WinMain` 函式之外，每個 Windows 傳統型應用程式還必須有視窗程序函式。 這個函式通常名為 `WndProc`。`WndProc` 具有下列語法。  
  
    ```  
    LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);  
    ```  
  
     這個函式可以處理應用程式從作業系統接收的許多*「訊息」*\(Message\)。 例如，假設應用程式有個對話方塊具有 \[確定\] 按鈕，當使用者按一下此按鈕時，作業系統會將按鈕已按下的訊息傳送給應用程式。`WndProc` 會負責回應該事件。 在此範例中，適當的回應可能會是關閉對話方塊。  
  
     如需詳細資訊，請參閱 [Window 程序](http://msdn.microsoft.com/library/windows/desktop/ms632593)。  
  
### 將功能加入 WinMain 函式中  
  
1.  在 `WinMain` 函式中，建立 [WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577) 類型的視窗類別結構。 這個結構會包含視窗的相關資訊，例如應用程式圖示、視窗的背景色彩、在標題列中顯示的名稱、視窗程序函式的名稱等。 下列範例會顯示一個典型的 `WNDCLASSEX` 結構。  
  
    ```  
    WNDCLASSEX wcex; wcex.cbSize = sizeof(WNDCLASSEX); wcex.style          = CS_HREDRAW | CS_VREDRAW; wcex.lpfnWndProc    = WndProc; wcex.cbClsExtra     = 0; wcex.cbWndExtra     = 0; wcex.hInstance      = hInstance; wcex.hIcon          = LoadIcon(hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); wcex.hCursor        = LoadCursor(NULL, IDC_ARROW); wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1); wcex.lpszMenuName   = NULL; wcex.lpszClassName  = szWindowClass; wcex.hIconSm        = LoadIcon(wcex.hInstance, MAKEINTRESOURCE(IDI_APPLICATION));  
    ```  
  
     如需這個結構之欄位的相關資訊，請參閱 [WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577)。  
  
2.  建立視窗類別之後，您必須予以註冊。 請使用 [RegisterClassEx](http://msdn.microsoft.com/library/windows/desktop/ms633587) 函式，並將視窗類別結構當做引數傳遞。  
  
    ```  
    if (!RegisterClassEx(&wcex)) { MessageBox(NULL, _T("Call to RegisterClassEx failed!"), _T("Win32 Guided Tour"), NULL); return 1; }  
    ```  
  
3.  現在您可以建立視窗。 請使用 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) 函式。  
  
    ```  
    static TCHAR szWindowClass[] = _T("win32app"); static TCHAR szTitle[] = _T("Win32 Guided Tour Application"); // The parameters to CreateWindow explained: // szWindowClass: the name of the application // szTitle: the text that appears in the title bar // WS_OVERLAPPEDWINDOW: the type of window to create // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y) // 500, 100: initial size (width, length) // NULL: the parent of this window // NULL: this application does not have a menu bar // hInstance: the first parameter from WinMain // NULL: not used in this application HWND hWnd = CreateWindow( szWindowClass, szTitle, WS_OVERLAPPEDWINDOW, CW_USEDEFAULT, CW_USEDEFAULT, 500, 100, NULL, NULL, hInstance, NULL ); if (!hWnd) { MessageBox(NULL, _T("Call to CreateWindow failed!"), _T("Win32 Guided Tour"), NULL); return 1; }  
    ```  
  
     這個函式會傳回 HWND，也就是視窗的控制代碼。 如需詳細資訊，請參閱 [Windows 資料類型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
4.  現在，使用下列程式碼來顯示視窗。  
  
    ```  
    // The parameters to ShowWindow explained: // hWnd: the value returned from CreateWindow // nCmdShow: the fourth parameter from WinMain ShowWindow(hWnd, nCmdShow); UpdateWindow(hWnd);  
    ```  
  
     此時顯示的視窗沒有太多內容，因為您還沒有實作 `WndProc` 函式。  
  
5.  現在加入訊息迴圈，以接聽作業系統所傳送的訊息。 當應用程式收到訊息時，這個迴圈會將它分派給 `WndProc` 函式以進行處理。 此訊息迴圈會類似下列程式碼。  
  
    ```  
    MSG msg; while (GetMessage(&msg, NULL, 0, 0)) { TranslateMessage(&msg); DispatchMessage(&msg); } return (int) msg.wParam;  
    ```  
  
     如需訊息迴圈中之結構和函式的詳細資訊，請參閱 [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958)、[GetMessage](http://msdn.microsoft.com/library/windows/desktop/ms644936)、[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。  
  
     此時的 `WinMain` 函式應該類似下列程式碼。  
  
    ```  
    int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow) { WNDCLASSEX wcex; wcex.cbSize = sizeof(WNDCLASSEX); wcex.style          = CS_HREDRAW | CS_VREDRAW; wcex.lpfnWndProc    = WndProc; wcex.cbClsExtra     = 0; wcex.cbWndExtra     = 0; wcex.hInstance      = hInstance; wcex.hIcon          = LoadIcon(hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); wcex.hCursor        = LoadCursor(NULL, IDC_ARROW); wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1); wcex.lpszMenuName   = NULL; wcex.lpszClassName  = szWindowClass; wcex.hIconSm        = LoadIcon(wcex.hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); if (!RegisterClassEx(&wcex)) { MessageBox(NULL, _T("Call to RegisterClassEx failed!"), _T("Win32 Guided Tour"), NULL); return 1; } hInst = hInstance; // Store instance handle in our global variable // The parameters to CreateWindow explained: // szWindowClass: the name of the application // szTitle: the text that appears in the title bar // WS_OVERLAPPEDWINDOW: the type of window to create // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y) // 500, 100: initial size (width, length) // NULL: the parent of this window // NULL: this application dows not have a menu bar // hInstance: the first parameter from WinMain // NULL: not used in this application HWND hWnd = CreateWindow( szWindowClass, szTitle, WS_OVERLAPPEDWINDOW, CW_USEDEFAULT, CW_USEDEFAULT, 500, 100, NULL, NULL, hInstance, NULL ); if (!hWnd) { MessageBox(NULL, _T("Call to CreateWindow failed!"), _T("Win32 Guided Tour"), NULL); return 1; } // The parameters to ShowWindow explained: // hWnd: the value returned from CreateWindow // nCmdShow: the fourth parameter from WinMain ShowWindow(hWnd, nCmdShow); UpdateWindow(hWnd); // Main message loop: MSG msg; while (GetMessage(&msg, NULL, 0, 0)) { TranslateMessage(&msg); DispatchMessage(&msg); } return (int) msg.wParam; }  
    ```  
  
### 將功能加入 WndProc 函式中  
  
1.  若要讓 `WndProc` 函式處理應用程式所接收的訊息，請實作 switch 陳述式。  
  
     第一個要處理的訊息是 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 訊息。 當應用程式所顯示的視窗有某部分必須更新時，應用程式就會收到這個訊息 \(第一次顯示視窗時，整個視窗都必須更新\)。  
  
     若要處理 `WM_PAINT` 訊息，請先呼叫 [BeginPaint](http://msdn.microsoft.com/library/windows/desktop/dd183362)，然後處理用以配置視窗中文字、按鈕和其他控制項的所有邏輯，再呼叫 [EndPaint](http://msdn.microsoft.com/library/windows/desktop/dd162598)。 對這個應用程式而言，起始呼叫與結束呼叫之間的邏輯是為了 在視窗中顯示 "Hello, World\!" 字串。 請注意，下列程式碼使用 [TextOut](http://msdn.microsoft.com/library/windows/desktop/dd145133) 函式來顯示字串。  
  
    ```  
    PAINTSTRUCT ps; HDC hdc; TCHAR greeting[] = _T("Hello, World!"); switch (message) { case WM_PAINT: hdc = BeginPaint(hWnd, &ps); // Here your application is laid out. // For this introduction, we just print out "Hello, World!" // in the top left corner. TextOut(hdc, 5, 5, greeting, _tcslen(greeting)); // End application-specific layout section. EndPaint(hWnd, &ps); break; }  
    ```  
  
2.  一個應用程式通常會處理許多其他訊息，例如 [WM\_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619) 和 [WM\_DESTROY](http://msdn.microsoft.com/library/windows/desktop/ms632620)。 下列程式碼會顯示基本但完整的 `WndProc` 函式。  
  
    ```  
    LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam) { PAINTSTRUCT ps; HDC hdc; TCHAR greeting[] = _T("Hello, World!"); switch (message) { case WM_PAINT: hdc = BeginPaint(hWnd, &ps); // Here your application is laid out. // For this introduction, we just print out "Hello, World!" // in the top left corner. TextOut(hdc, 5, 5, greeting, _tcslen(greeting)); // End application specific layout section. EndPaint(hWnd, &ps); break; case WM_DESTROY: PostQuitMessage(0); break; default: return DefWindowProc(hWnd, message, wParam, lParam); break; } return 0; }  
    ```  
  
##  <a name="example"></a> 範例  
  
#### 建立這個範例  
  
1.  如本逐步解說稍早的＜建立 Win32 專案＞所示，建立 Win32 專案。  
  
2.  複製這些步驟之後的程式碼，然後貼到 GT\_HelloWorldWin32.cpp 原始程式檔。  
  
3.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
4.  若要執行應用程式，請按 F5 鍵。 內含 "Hello World\!" 文字的視窗 應該會出現在顯示畫面的左上角。  
  
### 程式碼  
  
```  
// GT_HelloWorldWin32.cpp // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c #include <windows.h> #include <stdlib.h> #include <string.h> #include <tchar.h> // Global variables // The main window class name. static TCHAR szWindowClass[] = _T("win32app"); // The string that appears in the application's title bar. static TCHAR szTitle[] = _T("Win32 Guided Tour Application"); HINSTANCE hInst; // Forward declarations of functions included in this code module: LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM); int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow) { WNDCLASSEX wcex; wcex.cbSize = sizeof(WNDCLASSEX); wcex.style          = CS_HREDRAW | CS_VREDRAW; wcex.lpfnWndProc    = WndProc; wcex.cbClsExtra     = 0; wcex.cbWndExtra     = 0; wcex.hInstance      = hInstance; wcex.hIcon          = LoadIcon(hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); wcex.hCursor        = LoadCursor(NULL, IDC_ARROW); wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1); wcex.lpszMenuName   = NULL; wcex.lpszClassName  = szWindowClass; wcex.hIconSm        = LoadIcon(wcex.hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); if (!RegisterClassEx(&wcex)) { MessageBox(NULL, _T("Call to RegisterClassEx failed!"), _T("Win32 Guided Tour"), NULL); return 1; } hInst = hInstance; // Store instance handle in our global variable // The parameters to CreateWindow explained: // szWindowClass: the name of the application // szTitle: the text that appears in the title bar // WS_OVERLAPPEDWINDOW: the type of window to create // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y) // 500, 100: initial size (width, length) // NULL: the parent of this window // NULL: this application does not have a menu bar // hInstance: the first parameter from WinMain // NULL: not used in this application HWND hWnd = CreateWindow( szWindowClass, szTitle, WS_OVERLAPPEDWINDOW, CW_USEDEFAULT, CW_USEDEFAULT, 500, 100, NULL, NULL, hInstance, NULL ); if (!hWnd) { MessageBox(NULL, _T("Call to CreateWindow failed!"), _T("Win32 Guided Tour"), NULL); return 1; } // The parameters to ShowWindow explained: // hWnd: the value returned from CreateWindow // nCmdShow: the fourth parameter from WinMain ShowWindow(hWnd, nCmdShow); UpdateWindow(hWnd); // Main message loop: MSG msg; while (GetMessage(&msg, NULL, 0, 0)) { TranslateMessage(&msg); DispatchMessage(&msg); } return (int) msg.wParam; } // //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM) // //  PURPOSE:  Processes messages for the main window. // //  WM_PAINT    - Paint the main window //  WM_DESTROY  - post a quit message and return // // LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam) { PAINTSTRUCT ps; HDC hdc; TCHAR greeting[] = _T("Hello, World!"); switch (message) { case WM_PAINT: hdc = BeginPaint(hWnd, &ps); // Here your application is laid out. // For this introduction, we just print out "Hello, World!" // in the top left corner. TextOut(hdc, 5, 5, greeting, _tcslen(greeting)); // End application-specific layout section. EndPaint(hWnd, &ps); break; case WM_DESTROY: PostQuitMessage(0); break; default: return DefWindowProc(hWnd, message, wParam, lParam); break; } return 0; }  
```  
  
## 請參閱  
 [Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)