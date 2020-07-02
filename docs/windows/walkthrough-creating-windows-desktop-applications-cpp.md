---
title: 逐步解說：建立傳統 Windows 桌面應用程式（c + +）
description: 如何使用 Visual Studio、c + + 和 WIN32 API 建立最小的傳統 Windows 桌面應用程式
ms.custom: get-started-article
ms.date: 05/28/2020
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: 1b084cab0e985f9ab8c593e22d972913130e4380
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813605"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>逐步解說：建立傳統 Windows 桌面應用程式（c + +）

本逐步解說示範如何在 Visual Studio 中建立傳統的 Windows 桌面應用程式。 您將建立的範例應用程式會使用 Windows API 來顯示 "Hello，Windows desktop！" 視窗中顯示 "Hello, World!" 的基本 Windows 傳統型應用程式。 您可以使用在這個逐步解說中開發的程式碼作為模式，來建立其他 Windows 傳統型應用程式。

Windows API （也稱為 WIN32 API、Windows 桌面 API 和 Windows Classic API）是以 C 語言為基礎的架構，用於建立 Windows 應用程式。 它已經存在於二十年代之後，並已用來建立數十年的 Windows 應用程式。 Windows API 之上建了更先進且更簡單的程式架構。 例如，MFC、ATL、.NET framework。 即使是以 c + +/WinRT 撰寫之 UWP 和 Store 應用程式的最新的 Windows 執行階段程式碼，還是會使用底下的 Windows API。 如需 Windows API 的詳細資訊，請參閱[WINDOWS Api 索引](/windows/win32/apiindex/windows-api-list)。 建立 Windows 應用程式的方法有很多種，但上述流程是第一個。

> [!IMPORTANT]
> 為了簡潔起見，文字中會省略一些程式碼語句。 本檔結尾處的[組建程式碼](#build-the-code)區段會顯示完整的程式碼。

## <a name="prerequisites"></a>必要條件

- 執行 Microsoft Windows 7 或更新版本的電腦。 建議使用 Windows 10 以獲得最佳開發體驗。

- Visual Studio 的複本。 如需如何下載並安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確認已選取**使用 C++ 的桌面開發**工作負載。 如果您在安裝 Visual Studio 時未安裝此工作負載，也不用擔心。 您可以再次執行安裝程式並立即安裝。

   ![使用 C++ 開發桌面](../build/media/desktop-development-with-cpp.png "使用 C++ 的傳統型開發")

- 了解使用 Visual Studio IDE 的基本概念。 如果您先前使用過 Windows 傳統型應用程式，您應能輕鬆跟上。 如需簡介，請參閱 [Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- 了解足夠的 C++ 語言基本概念。 別擔心，我們不會進行太複雜的操作。

## <a name="create-a-windows-desktop-project"></a>建立 Windows 桌面專案

請遵循下列步驟來建立您的第一個 Windows 桌面專案。 當您執行時，您會輸入適用于運作中 Windows 桌面應用程式的程式碼。 若要查看您慣用版本 Visual Studio 的檔，請使用**版本**選取器控制項。 您可在此頁面的目錄頂端找到該檔案。

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立 Windows 桌面專案

1. 從主功能表，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話方塊頂端，將 [**語言**] 設定為**c + +**，將 [**平臺**] 設定為 [ **Windows**]，並將 [**專案類型**] 設定為 [**桌面**]

1. 從篩選過的專案類型清單中，選擇 [ **Windows 桌面 Wizard]** ，然後選擇 **[下一步**]。 在下一個頁面中，輸入專案的名稱，例如*DesktopApp*。

1. 選擇 [建立] **** 按鈕以建立專案。

1. 此時會出現 [ **Windows 桌面專案**] 對話方塊。 在 [**應用程式類型**] 底下，選取 **[桌面應用程式（.exe）**]。 在 [其他選項] **** 下，選取 [空專案] ****。 選擇 [**確定]** 以建立專案。

1. 在**方案總管**中，以滑鼠右鍵按一下**DesktopApp**專案，選擇 [**加入**]，然後選擇 [**新增專案**]。

   ![將新專案新增至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-153.gif "將新專案新增至 DesktopApp 專案")

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。 在 [**名稱**] 方塊中，輸入檔案的名稱，例如*HelloWindowsDesktop。* 選擇 [**新增**]。

   ![將 .cpp 檔案加入至 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-153.png "將 .cpp 檔案加入至 DesktopApp 專案")

現在已建立您的專案，並在編輯器中開啟您的原始程式檔。 若要繼續，請直接跳到[建立程式碼](#create-the-code)。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立 Windows 桌面專案

1. 在 [檔案]**** 功能表上，選擇 [新增]**** 然後選擇 [專案]****。

1. 在 [**新增專案**] 對話方塊的左窗格中，展開 [**已安裝**的  >  **Visual C++**]，然後選取 [ **Windows 桌面**]。 在中間窗格中，選取 [ **Windows 桌面 Wizard]**。

   在 [**名稱**] 方塊中，輸入專案的名稱，例如*DesktopApp*。 選擇 [確定]。

   ![將 DesktopApp 專案命名為](../build/media/desktop-app-new-project-name-153.png "將 DesktopApp 專案命名為")

1. 在 [ **Windows 桌面專案**] 對話方塊的 [**應用程式類型**] 底下，選取 **[Windows 應用程式（.exe）**]。 在 [其他選項] **** 下，選取 [空專案] ****。 請確定未選取先行**編譯頭**檔。 選擇 [**確定]** 以建立專案。

1. 在**方案總管**中，以滑鼠右鍵按一下**DesktopApp**專案，選擇 [**加入**]，然後選擇 [**新增專案**]。

   ![將新專案新增至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-153.gif "將新專案新增至 DesktopApp 專案")

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。 在 [**名稱**] 方塊中，輸入檔案的名稱，例如*HelloWindowsDesktop。* 選擇 [**新增**]。

   ![將 .cpp 檔案加入至 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-153.png "將 .cpp 檔案加入至 DesktopApp 專案")

現在已建立您的專案，並在編輯器中開啟您的原始程式檔。 若要繼續，請直接跳到[建立程式碼](#create-the-code)。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>在 Visual Studio 2015 中建立 Windows 桌面專案

1. 在 [檔案]**** 功能表上，選擇 [新增]**** 然後選擇 [專案]****。

1. 在 [**新增專案**] 對話方塊的左窗格中，展開 [**已安裝**  >  的**範本**]  >  **Visual C++**，然後選取 [ **Win32**]。 在中間窗格選取 [Win32 專案] ****。

   在 [**名稱**] 方塊中，輸入專案的名稱，例如*DesktopApp*。 選擇 [確定]。

   ![將 DesktopApp 專案命名為](../build/media/desktop-app-new-project-name-150.png "將 DesktopApp 專案命名為")

1. 在**Win32 應用程式精靈**的 [**總覽**] 頁面上，選擇 [**下一步]**。

   ![在 Win32 應用程式中建立 DesktopApp 總覽](../build/media/desktop-app-win32-wizard-overview-150.png "在 Win32 應用程式中建立 DesktopApp 總覽")

1. 在 [**應用程式設定**] 頁面的 [**應用程式類型**] 底下，選取 [ **Windows 應用程式**]。 在 [**其他選項**] 底下，取消核取 [先行**編譯頭**檔]，然後選取 [**空白** 選擇 **[完成]** 以建立專案。

1. 在**方案總管**中，以滑鼠右鍵按一下 DesktopApp 專案，選擇 [**加入**]，然後選擇 [**新增專案**]。

   ![將新專案新增至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-150.gif "將新專案新增至 DesktopApp 專案")

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。 在 [**名稱**] 方塊中，輸入檔案的名稱，例如*HelloWindowsDesktop。* 選擇 [**新增**]。

   ![將 .cpp 檔案加入至 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-150.png "將 .cpp 檔案加入至 DesktopApp 專案")

現在已建立您的專案，並在編輯器中開啟您的原始程式檔。

::: moniker-end

## <a name="create-the-code"></a>建立程式碼

接下來，您將瞭解如何在 Visual Studio 中建立 Windows 桌面應用程式的程式碼。

### <a name="to-start-a-windows-desktop-application"></a>啟動 Windows 傳統型應用程式

1. 就像每個 C 應用程式和 c + + 應用程式都必須有函式做 `main` 為其起點，每個 Windows 桌面應用程式都必須有函式 `WinMain` 。 `WinMain` 具有下列語法。

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   如需此函式之參數和傳回值的相關資訊，請參閱[WinMain 進入點](/windows/win32/api/winbase/nf-winbase-winmain)。

   > [!NOTE]
   > 所有這些額外的字組，例如 `CALLBACK` 、或 `HINSTANCE` ，或 `_In_` ？ 傳統的 Windows API 會廣泛地使用 typedef 和預處理器宏來抽象化一些類型的詳細資料，以及平臺特定的程式碼，例如呼叫慣例、 **__declspec**宣告和編譯器 pragma。 在 Visual Studio 中，您可以使用 IntelliSense [[快速](/visualstudio/ide/using-intellisense#quick-info)諮詢] 功能來查看這些 typedef 和巨集定義的內容。 將滑鼠暫留在感對的單字上，或選取它，然後按**ctrl** + **K**、 **ctrl** + **I** ，尋找包含定義的小型快顯視窗。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。 參數和傳回類型通常會使用*SAL 注釋*，以協助您攔截程式設計錯誤。 如需詳細資訊，請參閱[使用 SAL 注釋減少 C/c + + 程式碼](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)缺失。

1. Windows 桌面程式需要 &lt; windows>。 &lt;> tchar 會定義 `TCHAR` 宏，這會在專案中定義 UNICODE 符號時，最後解析成**wchar_t** ，否則會解析成**char**。  如果您一直使用 UNICODE 建立，則不需要 TCHAR，而且可以直接使用**wchar_t** 。

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. 除了函 `WinMain` 式之外，每個 Windows 桌面應用程式也必須有一個視窗程式功能。 此函式通常會命名為 `WndProc` ，但您可以將它命名為任何您喜歡的名稱。 `WndProc` 具有下列語法。

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   在此函式中，您會撰寫程式碼，以處理當發生*事件*時，應用程式從 Windows 接收的*訊息*。 例如，如果使用者在您的應用程式中選擇 [確定] 按鈕，Windows 就會傳送訊息給您，而您可以在函式內撰寫可 `WndProc` 執行任何適當工作的程式碼。 它稱為「*處理*事件」。 您只會處理與您的應用程式相關的事件。

   如需詳細資訊，請參閱 [Window 程序](/windows/win32/winmsg/window-procedures)。

### <a name="to-add-functionality-to-the-winmain-function"></a>將功能加入 WinMain 函式中

1. 在函式中 `WinMain` ，您會填入[WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw)類型的結構。 結構包含視窗的相關資訊：應用程式圖示、視窗的背景色彩、要在標題列中顯示的名稱，還有其他專案。 重要的是，它包含您的視窗程式的函式指標。 下列範例會顯示一個典型的 `WNDCLASSEX` 結構。

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   如需上述結構欄位的詳細資訊，請參閱[WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw)。

1. 向 Windows 註冊， `WNDCLASSEX` 讓它知道您的視窗，以及如何傳送訊息給它。 請使用 [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) 函式，並將視窗類別結構當做引數傳遞。 `_T`因為我們使用型別，所以會使用宏 `TCHAR` 。

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. 現在您可以建立視窗。 請使用 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 函式。

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   此函式 `HWND` 會傳回，也就是視窗的控制碼。 控制碼有點像是 Windows 用來追蹤已開啟視窗的指標。 如需詳細資訊，請參閱 [Windows 資料類型](/windows/win32/WinProg/windows-data-types)。

1. 此時，已建立視窗，但我們仍需要告訴 Windows 使其顯示。 這就是此程式碼的作用：

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   顯示的視窗沒有太多內容，因為您尚未實作為函式 `WndProc` 。 換句話說，應用程式尚未處理 Windows 現在傳送給它的訊息。

1. 若要處理訊息，我們會先新增訊息迴圈來接聽 Windows 所傳送的訊息。 當應用程式收到訊息時，此迴圈會將它分派至要處理的函式 `WndProc` 。 此訊息迴圈會類似下列程式碼。

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   如需訊息迴圈中之結構和函式的詳細資訊，請參閱 [MSG](/windows/win32/api/winuser/ns-winuser-msg)、 [GetMessage](/windows/win32/api/winuser/nf-winuser-getmessage)、 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)。

   此時的 `WinMain` 函式應該類似下列程式碼。

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>將功能加入 WndProc 函式中

1. 若要讓 `WndProc` 函式處理應用程式所接收的訊息，請實作 switch 陳述式。

   其中一個要處理的重要訊息是[WM_PAINT](/windows/win32/gdi/wm-paint)訊息。 應用程式會在 `WM_PAINT` 部分顯示的視窗必須更新時收到訊息。 當使用者在視窗前方移動視窗時，就會發生此事件，然後再將它移開。 您的應用程式不知道這些事件發生的時間。 只有 Windows 知道，因此它會使用訊息來通知您的應用程式 `WM_PAINT` 。 當視窗第一次顯示時，所有必須更新。

   若要處理 `WM_PAINT` 訊息，請先呼叫 [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint)，然後處理用以配置視窗中文字、按鈕和其他控制項的所有邏輯，再呼叫 [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint)。 針對應用程式，開始呼叫和結束呼叫之間的邏輯會顯示 "Hello，Windows desktop！" 字串。 在視窗中顯示 "Hello, World!" 字串。 在下列程式碼中， [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw)函數是用來顯示字串。

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC`在程式碼中，是裝置內容的控制碼，用來在視窗的工作區中繪製。 使用和函式 `BeginPaint` `EndPaint` 來準備和完成工作區中的繪圖。 `BeginPaint`傳回用來在工作區中繪製的顯示裝置內容控制碼。`EndPaint`結束繪製要求並釋放裝置內容。

1. 應用程式通常會處理許多其他訊息。 例如，在第一次建立視窗時[WM_CREATE](/windows/win32/winmsg/wm-create) ，並在視窗關閉時[WM_DESTROY](/windows/win32/winmsg/wm-destroy) 。 下列程式碼會顯示基本但完整的 `WndProc` 函式。

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>建置程式碼

依照承諾，以下是適用于工作應用程式的完整程式碼。

### <a name="to-build-this-example"></a>建立這個範例

1. 在編輯器中刪除您在*HelloWindowsDesktop*中輸入的任何程式碼。 將此範例程式碼複製並貼到*HelloWindowsDesktop*中：

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。 編譯的結果應該會出現在 Visual Studio 的 [**輸出**] 視窗中。

   ![建立 DesktopApp 專案](../build/media/desktop-app-project-build-150.gif "建立 DesktopApp 專案")

1. 若要執行應用程式，請按 **F5**。 包含文字 "Hello，Windows desktop！" 的視窗 應該會出現在顯示畫面的左上角。

   ![執行 DesktopApp 專案](../build/media/desktop-app-project-run-157.PNG "執行 DesktopApp 專案")

恭喜！ 您已完成此逐步解說，並建立了傳統的 Windows 桌面應用程式。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)
