---
title: 逐步解說： 建立傳統 Windows 桌面應用程式 （c + +） |Microsoft 文件
ms.custom: get-started-article
ms.date: 1/11/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e5581292ec163a2e745802c66a87c14a8457f141
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>逐步解說： 建立傳統 Windows 桌面應用程式 （c + +）

本逐步解說示範如何在 Visual Studio 中建立傳統 Windows 桌面應用程式。 您將建立範例應用程式使用 Windows API 來顯示"Hello，Windows 桌面"！ 視窗中顯示 "Hello, World!" 的基本 Windows 傳統型應用程式。 您可以使用在這個逐步解說中開發的程式碼作為模式，來建立其他 Windows 傳統型應用程式。

Windows API （也稱為 Win32 應用程式開發介面、 Windows 桌面應用程式開發介面和 Windows 傳統應用程式開發介面） 是用來建立 Windows 應用程式的 C 語言的基礎架構。 它已自 1980年存在，而且已經用來建立 Windows 應用程式的數十年。 已在此應用程式開發介面，例如 MFC、 ATL 和.NET frameworks 之上建置更進階的和更容易程式的架構。 即使大多數最新型的程式碼適用 UWP 和市集應用程式撰寫的 C + + WinRT 會使用下面這個 API。 如需 Windows API 的詳細資訊，請參閱[Windows 應用程式開發介面索引](https://msdn.microsoft.com/library/windows/desktop/ff818516.aspx)。 有許多方法可以建立 Windows 應用程式，但這是第一個。

> [!IMPORTANT]
> 為了簡短起見，在文字中省略某些程式碼陳述式。 [建置程式碼](#build-the-code)這份文件最後一節顯示完整的程式碼。

## <a name="prerequisites"></a>必要條件

- 執行 Microsoft Windows 7 或更新版本的電腦。 我們建議最佳的開發經驗 Windows 10。

- Visual Studio 2017 的複本。 如需如何下載並安裝 Visual Studio，請參閱[安裝 Visual Studio 2017](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確定**的 c + + 桌面應用程式開發**會檢查工作負載。 如果您未安裝此工作負載，當您安裝 Visual Studio 不要擔心。 您可以再次執行安裝程式，並立即安裝。

   ![使用 c + + 桌面開發](../build/media/desktop-development-with-cpp.png "的 c + + 桌面應用程式開發")

- 了解使用 Visual Studio IDE 的基本概念。 如果您使用 Windows 桌面應用程式之前，您可能可以跟上。 如需簡介，請參閱[Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- 足夠要遵循的 c + + 語言基本知識的了解。 別擔心，我們通常不太複雜的任何項目。

## <a name="create-a-windows-desktop-project"></a>建立 Windows 桌面專案

請遵循下列步驟建立第一個 Windows 桌面專案，並可運作的 Windows 桌面應用程式輸入的代碼。 如果您使用 Visual Studio 的 Visual Studio 2017 版本 15.3 比舊的版本，跳到[建立 Windows 桌面專案在 Visual Studio 2017 RTM](#create-in-vs2017-rtm)。

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>若要建立 Windows 桌面專案在 Visual Studio 2017 更新 15.3 和更新版本

1. 在 [檔案] 功能表上，選擇 [新增] 然後選擇 [專案]。

1. 在**新專案**對話方塊的左窗格中，展開 **已安裝**， **Visual c + +**，然後選取**Windows 桌面**。 在中間窗格中，選取**Windows 桌面精靈**。

   在**名稱**方塊中，輸入專案的名稱，例如*DesktopApp*。 選擇 [確定] 。

   ![DesktopApp 專案的名稱，](../build/media/desktop-app-new-project-name-153.png "DesktopApp 專案的名稱")

1. 在**Windows 桌面專案**對話方塊下方**應用程式類型**，選取**Windows 應用程式 (.exe)**。 在 [其他選項] 下，選取 [空專案] 。 選擇**確定**建立專案。

   ![在 Windows 桌面專案精靈 建立 DesktopApp](../build/media/desktop-app-new-project-wizard-153.png "DesktopApp 建立在 Windows 桌面專案精靈")

1. 在**方案總管] 中**，以滑鼠右鍵按一下**DesktopApp**專案，選擇**新增**，然後選擇 [**新項目**。

   ![加入新項目至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-153.gif "DesktopApp 專案加入新項目")

1. 在 [加入新項目]  對話方塊中，選取 [C++ 檔 (.cpp)] 。 在**名稱**方塊中，輸入檔案名稱，例如*HelloWindowsDesktop.cpp*。 選擇 [新增]。

   ![將.cpp 檔案，加入 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-153.png "將.cpp 檔案，加入 DesktopApp 專案")

現在已建立專案，並在編輯器中開啟原始程式檔。 若要繼續，請直接前往[建立程式碼](#create-the-code)。

### <a id="create-in-vs2017-rtm"></a> 若要在 Visual Studio 2017 RTM 中建立 Windows 桌面專案

1. 在 [檔案] 功能表上，選擇 [新增] 然後選擇 [專案]。

1. 在**新專案**對話方塊的左窗格中，展開 **已安裝**，**範本**， **Visual c + +**，然後選取  **Win32**。 在中間窗格選取 [Win32 專案] 。

   在**名稱**方塊中，輸入專案的名稱，例如*DesktopApp*。 選擇 [確定] 。

   ![DesktopApp 專案的名稱，](../build/media/desktop-app-new-project-name-150.png "DesktopApp 專案的名稱")

1. 在**概觀**頁面**Win32 應用程式精靈**，選擇**下一步**。

   ![建立 Win32 應用程式精靈概觀 DesktopApp](../build/media/desktop-app-win32-wizard-overview-150.png "DesktopApp 建立 Win32 應用程式精靈概觀")

1. 在**應用程式設定**頁面的 **應用程式類型**，選取**Windows 應用程式**。 在 [其他選項] 下，選取 [空專案] 。 選擇**完成**建立專案。

   ![在 Win32 應用程式精靈 設定中建立 DesktopApp](../build/media/desktop-app-win32-wizard-settings-150.png "DesktopApp 建立 Win32 應用程式精靈設定中")

1. 在**方案總管] 中**，以滑鼠右鍵按一下 DesktopApp 專案，選擇**新增**，然後選擇 [**新項目**。

   ![加入新項目至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-150.gif "DesktopApp 專案加入新項目")

1. 在 [加入新項目]  對話方塊中，選取 [C++ 檔 (.cpp)] 。 在**名稱**方塊中，輸入檔案名稱，例如*HelloWindowsDesktop.cpp*。 選擇 [新增]。

   ![將.cpp 檔案，加入 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-150.png "將.cpp 檔案，加入 DesktopApp 專案")

現在已建立專案，並在編輯器中開啟原始程式檔。

## <a name="create-the-code"></a>建立程式碼

接下來，您將學習如何在 Visual Studio 中建立 Windows 傳統型應用程式的程式碼。

### <a name="to-start-a-windows-desktop-application"></a>啟動 Windows 傳統型應用程式

1. 就像每個 C 應用程式和 c + + 應用程式必須有`main`函式做為起點，每個 Windows 桌面應用程式必須具有`WinMain`函式。 `WinMain` 具有下列語法。

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   參數和傳回值，這個函式的相關資訊，請參閱[WinMain 進入點](https://msdn.microsoft.com/library/windows/desktop/ms633559)。

   > [!NOTE]
   > 什麼是所有這些額外字，例如**回呼**，或**HINSTANCE**，或**\_中\_**？ 傳統的 Windows API 所使用的 typedef 和廣泛地提取出前置處理器巨集的某些細節的型別和特定平台程式碼，呼叫慣例，例如 **__declspec**宣告和編譯器的 pragma。 在 Visual Studio 中，您可以使用 IntelliSense[快速諮詢](/visualstudio/ide/using-intellisense#quick-info)功能，請參閱什麼這些 typedef 和巨集定義。 滑鼠停留的感興趣，word 或選取它，然後按下 ctrl-K、 ctrl-我的小型的快顯視窗，其中包含定義。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。 參數和傳回型別通常會使用*SAL 註釋*可協助您捕捉程式設計錯誤。 如需詳細資訊，請參閱[使用 SAL 註釋減少 C/c + + 程式碼缺失](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)。

1. Windows 桌面程式需要&lt;windows.h >。 &lt;tchar.h > 定義`TCHAR`巨集，它最終會解析至`wchar_t`如果您的專案中定義 UNICODE symbol，否則它會解析為`char`。  如果是一律以啟用 UNICODE，您不需要 TCHAR，並只可以直接使用 wchar_t。

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. 除了 `WinMain` 函式之外，每個 Windows 傳統型應用程式還必須有視窗程序函式。 此函式通常會命名為`WndProc`但您可以將檔案命名任何您喜歡。 `WndProc` 具有下列語法。

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   在這個函式中，您撰寫程式碼來處理*訊息*應用程式接收來自 Windows 時*事件*發生。 比方說，如果使用者在應用程式中，選擇 [確定] 按鈕，Windows 會將訊息傳送給您，而且您可以撰寫程式碼內您`WndProc`沒有任何工作是適當的函式。 這稱為*處理*事件。 您只需要處理您的應用程式相關的事件。

   如需詳細資訊，請參閱[視窗程序](https://msdn.microsoft.com/library/windows/desktop/ms632593)。

### <a name="to-add-functionality-to-the-winmain-function"></a>將功能加入 WinMain 函式中

1. 在`WinMain`函式，填入型別的結構[WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577)。 此結構包含視窗，例如，應用程式圖示，視窗中，要顯示在標題列，並非常重要的是，您的視窗程序的函式指標的名稱的背景色彩的相關資訊。 下列範例會顯示一個典型的 `WNDCLASSEX` 結構。

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

   此結構欄位的詳細資訊，請參閱[WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577)。

1. 您必須註冊`WNDCLASSEX`與 Windows，讓它知道您的視窗，以及如何將訊息傳送給它。 使用[RegisterClassEx](https://msdn.microsoft.com/library/windows/desktop/ms633587)函式，並將視窗類別結構當做引數。 `_T`巨集使用，因為我們使用`TCHAR`型別。

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

1. 現在您可以建立視窗。 使用[CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679)函式。

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

   此函數會傳回`HWND`，這是視窗的控制代碼。 控點是有些許類似，Windows 會用來追蹤開啟的視窗的指標。 如需詳細資訊，請參閱[Windows 資料類型](https://msdn.microsoft.com/library/windows/desktop/aa383751)。

1. 此時已建立的視窗，但我們仍需要告訴 Windows 設為可見。 也就是此程式碼的:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   顯示的視窗不具有太多內容，因為尚未實作`WndProc`函式。 換句話說，應用程式，並不會尚未處理 Windows 現在正在傳送給它的訊息。

1. 若要處理的訊息，我們會先新增接聽 Windows 會傳送訊息的訊息迴圈。 當應用程式接收訊息時，此迴圈會分派到您`WndProc`函式以進行處理。 此訊息迴圈會類似下列程式碼。

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   如需結構和訊息迴圈中的函式的詳細資訊，請參閱[MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958)， [GetMessage](https://msdn.microsoft.com/library/windows/desktop/ms644936)， [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955)，和[DispatchMessage](https://msdn.microsoft.com/library/windows/desktop/ms644934).

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

   一個重要的訊息處理是[WM_PAINT](https://msdn.microsoft.com/library/windows/desktop/dd145213)訊息。 當應用程式所顯示的視窗有某部分必須更新時，應用程式就會收到這個訊息 當使用者移動視窗中，前面的視窗，然後將它移開一次，可能會發生此事件。 您的應用程式並不知道這類事件發生時。只有 Windows 知道，所以它會通知您與`WM_PAINT`。 第一次顯示視窗，必須更新所有內容。

   若要處理`WM_PAINT`訊息、 第一次呼叫[BeginPaint](https://msdn.microsoft.com/library/windows/desktop/dd183362)，然後處理配置時文字、 按鈕和其他控制項在視窗中，所有的邏輯，然後呼叫[EndPaint](https://msdn.microsoft.com/library/windows/desktop/dd162598)。 此應用程式，開始與結束呼叫之間的邏輯是顯示字串"Hello，Windows 桌面"！ 在視窗中顯示 "Hello, World!" 字串。 下列程式碼，請注意， [TextOut](https://msdn.microsoft.com/library/windows/desktop/dd145133)函數用來顯示字串。

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

   `HDC` 在這段程式碼是裝置內容，也就是 Windows 用來啟用與圖形子系統進行通訊的應用程式的資料結構的控制代碼。 `BeginPaint`和`EndPaint`函式會確保您的應用程式行為都像是一個優良，而且不會使用超出它所需要的裝置內容。 這有助於確保圖形子系統是可供其他應用程式。

1. 應用程式通常會處理許多其他訊息，例如[WM_CREATE](https://msdn.microsoft.com/library/windows/desktop/ms632619)時第一次建立一個視窗，和[WM_DESTROY](https://msdn.microsoft.com/library/windows/desktop/ms632620)視窗關閉時。 下列程式碼會顯示基本但完整的 `WndProc` 函式。

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

我們承諾給，以下是可用的應用程式的完整程式碼。

### <a name="to-build-this-example"></a>建立這個範例

1. 刪除您已經在編輯器中輸入 HelloWindowsDesktop.cpp 中的任何程式碼。 此範例程式碼複製並貼到 HelloWindowsDesktop.cpp:

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
      _In_ HINSTANCE hPrevInstance,
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

1. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。 編譯的結果應該會出現在**輸出**Visual Studio 中的視窗。

   ![建置 DesktopApp 專案](../build/media/desktop-app-project-build-150.gif "建置 DesktopApp 專案")

1. 若要執行應用程式，請按**F5**。 視窗，其中包含文字"Hello，Windows 桌面"！ 應該會出現在顯示畫面的左上角。

   ![執行 DesktopApp 專案](../build/media/desktop-app-project-run-150.gif "執行 DesktopApp 專案")

恭喜您！ 當您完成此逐步解說中，並建置傳統 Windows 桌面應用程式。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)
