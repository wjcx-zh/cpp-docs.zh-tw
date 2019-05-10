---
title: 逐步解說：建立傳統 Windows 桌面應用程式 (C++)
ms.custom: get-started-article
ms.date: 04/23/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: 0bc9ef82863fde361964234cca54f12aac1e2abe
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877395"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>逐步解說：建立傳統 Windows 桌面應用程式 (C++)

本逐步解說示範如何在 Visual Studio 中建立傳統 Windows 桌面應用程式。 您將建立範例應用程式使用 Windows API 來顯示"Hello，Windows desktop"！ 視窗中顯示 "Hello, World!" 的基本 Windows 傳統型應用程式。 您可以使用在這個逐步解說中開發的程式碼作為模式，來建立其他 Windows 傳統型應用程式。

Windows API （也稱為 Win32 API、 Windows 桌面 API 和 Windows 的傳統 API） 是 C 語言為基礎的架構，用於建立 Windows 應用程式。 它已從 1980 年代，並已用來建立 Windows 應用程式數十年。 更進階且更容易程式的架構已建置的 Windows API，例如 MFC、 ATL 和.NET framework 之上。 即使是最新式的程式碼撰寫的 UWP 和市集應用程式的C++/WinRT 使用下方的 Windows API。 如需有關 Windows API 的詳細資訊，請參閱 < [Windows API 索引](/windows/desktop/apiindex/windows-api-list)。 有許多方式可建立 Windows 應用程式，但上述程序是第一個。

> [!IMPORTANT]
> 為了保持簡潔，省略某些程式碼陳述式文字中。 [建置程式碼](#build-the-code)這份文件結尾的區段會顯示完整的程式碼。

## <a name="prerequisites"></a>必要條件

- 執行 Microsoft Windows 7 或更新版本的電腦。 我們建議的最佳開發體驗的 Windows 10。

- Visual Studio 的複本。 如需如何下載並安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確定**使用的桌面開發C++** 會檢查工作負載。 別擔心，如果您在安裝 Visual Studio 時，未安裝此工作負載。 您可以再次執行安裝程式，並立即安裝。

   ![使用的桌面開發C++ ](../build/media/desktop-development-with-cpp.png "使用的桌面開發C++")

- 使用 Visual Studio IDE 的基本概念了解。 如果您已使用之前的 Windows 傳統型應用程式，您可能可以保留。 如需簡介，請參閱[Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- 足夠的基本概念了解C++若要跟著做的語言。 別擔心，我們不會有太過複雜。

## <a name="create-a-windows-desktop-project"></a>建立 Windows 桌面專案

請遵循下列步驟來建立第一個 Windows 桌面專案，並輸入可運作的 Windows 桌面應用程式程式碼。 請確定版本選擇器，此頁面的左上角設為 Visual Studio 所使用的正確版本。

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 建立 Windows 桌面專案

1. 從主功能表中，選擇**檔案** > **新增** > **專案**開啟**建立新的專案**對話方塊方塊。

1. 在對話方塊頂端，設定**語言**來**C++**，將**平台**至**Windows**，並將**專案類型**要**桌面**。 

1. 從 [專案類型的篩選清單，選擇**Windows Desktop 精靈**然後選擇**下一步]**。 在下一步 頁面中，輸入專案名稱，然後指定專案位置，如有需要。

1. 選擇**建立**按鈕，以建立專案。

1. **Windows 桌面專案** 對話方塊隨即顯示。 底下**應用程式類型**，選取**Windows 應用程式 (.exe)**。 在 [其他選項] 下，選取 [空專案] 。 選擇**確定**建立專案。

1. 中**方案總管 中**，以滑鼠右鍵按一下**DesktopApp**專案，選擇**新增**，然後選擇**新項目**。

   ![新增項目至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-153.gif "DesktopApp 專案加入新的項目")

1. 在 [加入新項目]  對話方塊中，選取 [C++ 檔 (.cpp)] 。 在 **名稱**方塊中，輸入檔案名稱，例如*HelloWindowsDesktop.cpp*。 選擇 [新增]。

   ![將.cpp 檔案，加入 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-153.png "DesktopApp 專案新增.cpp 檔案")

現在已建立您的專案，並在編輯器中開啟原始程式檔。 若要繼續，請直接跳到[建立的程式碼](#create-the-code)。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>若要在 Visual Studio 2017 中建立 Windows 桌面專案

1. 在 [檔案] 功能表上，選擇 [新增] 然後選擇 [專案]。

1. 在**新的專案**對話方塊中，在左窗格中，展開**已安裝** > **Visual C++** ，然後選取**Windows Desktop**. 在中間窗格中，選取**Windows Desktop 精靈**。

   在 **名稱**方塊中，輸入專案名稱，例如*DesktopApp*。 選擇 [確定] 。

   ![將專案命名為 DesktopApp](../build/media/desktop-app-new-project-name-153.png "DesktopApp 專案的名稱")

1. 在 [ **Windows 桌面專案**] 對話方塊底下**應用程式類型**，選取**Windows 應用程式 (.exe)**。 在 [其他選項] 下，選取 [空專案] 。 選擇**確定**建立專案。

   ![在 Windows 桌面專案精靈 建立 DesktopApp](../build/media/desktop-app-new-project-wizard-153.png "Windows 桌面專案精靈 建立 DesktopApp")

1. 中**方案總管 中**，以滑鼠右鍵按一下**DesktopApp**專案，選擇**新增**，然後選擇**新項目**。

   ![新增項目至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-153.gif "DesktopApp 專案加入新的項目")

1. 在 [加入新項目]  對話方塊中，選取 [C++ 檔 (.cpp)] 。 在 **名稱**方塊中，輸入檔案名稱，例如*HelloWindowsDesktop.cpp*。 選擇 [新增]。

   ![將.cpp 檔案，加入 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-153.png "DesktopApp 專案新增.cpp 檔案")

現在已建立您的專案，並在編輯器中開啟原始程式檔。 若要繼續，請直接跳到[建立的程式碼](#create-the-code)。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中建立 Windows 桌面專案

1. 在 [檔案] 功能表上，選擇 [新增] 然後選擇 [專案]。

1. 在 **新的專案**對話方塊中，在左窗格中，展開**已安裝** > **範本** > **Visual C++** ，然後選取**Win32**。 在中間窗格選取 [Win32 專案] 。

   在 **名稱**方塊中，輸入專案名稱，例如*DesktopApp*。 選擇 [確定] 。

   ![將專案命名為 DesktopApp](../build/media/desktop-app-new-project-name-150.png "DesktopApp 專案的名稱")

1. 在 [**概觀**頁**Win32 應用程式精靈**，選擇**下一步]**。

   ![在 Win32 應用程式精靈概觀中建立 DesktopApp](../build/media/desktop-app-win32-wizard-overview-150.png "DesktopApp 在 Win32 應用程式精靈概觀")

1. 在 **應用程式設定**頁面的 **應用程式類型**，選取**Windows 應用程式**。 在 [其他選項] 下，選取 [空專案] 。 選擇**完成**建立專案。

   ![在 Win32 應用程式精靈設定中建立 DesktopApp](../build/media/desktop-app-win32-wizard-settings-150.png "DesktopApp 在 Win32 應用程式精靈設定")

1. 中**方案總管] 中**，以滑鼠右鍵按一下 [DesktopApp 專案，然後選擇**新增**，然後選擇**新項目**。

   ![新增項目至 DesktopApp 專案](../build/media/desktop-app-project-add-new-item-150.gif "DesktopApp 專案加入新的項目")

1. 在 [加入新項目]  對話方塊中，選取 [C++ 檔 (.cpp)] 。 在 **名稱**方塊中，輸入檔案名稱，例如*HelloWindowsDesktop.cpp*。 選擇 [新增]。

   ![將.cpp 檔案，加入 DesktopApp 專案](../build/media/desktop-app-add-cpp-file-150.png "DesktopApp 專案新增.cpp 檔案")

現在已建立您的專案，並在編輯器中開啟原始程式檔。

::: moniker-end

## <a name="create-the-code"></a>建立程式碼

接下來，您將了解如何在 Visual Studio 中建立 Windows 桌面應用程式的程式碼。

### <a name="to-start-a-windows-desktop-application"></a>啟動 Windows 傳統型應用程式

1. 就如同每個 C 應用程式和C++應用程式必須有`main`函式做為起點，每個 Windows 桌面應用程式必須擁有`WinMain`函式。 `WinMain` 具有下列語法。

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   參數和傳回值，這個函式的相關資訊，請參閱[WinMain 進入點](/windows/desktop/api/winbase/nf-winbase-winmain)。

   > [!NOTE]
   > 什麼是所有這些額外字詞，例如`CALLBACK`，或`HINSTANCE`，或`_In_`？ 傳統的 Windows API 所使用的 typedef 和廣泛地抽離前置處理器巨集的一些詳細資料類型和特定平台程式碼，呼叫慣例，例如 **__declspec**宣告和編譯器的 pragma。 在 Visual Studio 中，您可以使用 IntelliSense[快速諮詢](/visualstudio/ide/using-intellisense#quick-info)功能，請參閱什麼這些 typedef 和巨集定義。 停留在感興趣的文字或選取它，然後按**Ctrl**+**K**， **Ctrl**+**我**的包含定義的小型快顯視窗。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。 參數和傳回型別通常會使用*SAL 註釋*可協助您捕捉程式設計錯誤。 如需詳細資訊，請參閱 <<c0> [ 使用 SAL 註釋減少 C /C++程式碼缺失](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)。</c0>

1. Windows 桌面程式需要&lt;windows.h >。 &lt;tchar.h > 定義`TCHAR`最終會解析巨集來**wchar_t**如果您的專案中定義的 UNICODE 符號，否則它會解析成**char**。  如果您一律使用來建置啟用 UNICODE，您不需要 TCHAR，並可以是直接使用**wchar_t**直接。

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. 除了 `WinMain` 函式之外，每個 Windows 傳統型應用程式還必須有視窗程序函式。 此函式通常會命名為`WndProc`但您可以為它命名您喜歡。 `WndProc` 具有下列語法。

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   在此函式中，您可以撰寫程式碼來處理*訊息*接收從 Windows 的應用程式時*事件*發生。 比方說，如果使用者選擇 [確定] 按鈕，在您的應用程式中，Windows 會將訊息傳送給您，而您可以撰寫程式碼內您`WndProc`會執行任何工作適當的函式。 它會呼叫*處理*事件。 您只需要處理您的應用程式相關的事件。

   如需詳細資訊，請參閱 [Window 程序](/windows/desktop/winmsg/window-procedures)。

### <a name="to-add-functionality-to-the-winmain-function"></a>將功能加入 WinMain 函式中

1. 在 `WinMain`函式中，填入類型的結構[WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa)。 此結構包含視窗，例如，應用程式圖示、 視窗中，要顯示在標題列中，和重要的是，您的視窗程序的函式指標的名稱的背景色彩的相關資訊。 下列範例會顯示一個典型的 `WNDCLASSEX` 結構。

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

   上述的結構欄位的詳細資訊，請參閱[WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa)。

1. 註冊`WNDCLASSEX`與 Windows，讓它知道有關您的視窗，以及如何將訊息傳送給它。 請使用 [RegisterClassEx](/windows/desktop/api/winuser/nf-winuser-registerclassexa) 函式，並將視窗類別結構當做引數傳遞。 `_T`巨集，因為我們使用`TCHAR`型別。

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

1. 現在您可以建立視窗。 請使用 [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) 函式。

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

   此函數會傳回`HWND`，這是視窗的控制代碼。 控制代碼會有些許類似 Windows 會使用要追蹤開啟的視窗的指標。 如需詳細資訊，請參閱 [Windows 資料類型](/windows/desktop/WinProg/windows-data-types)。

1. 此時，已建立的視窗，但我們仍需要告知要顯示的 Windows。 這就是此程式碼的:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   顯示的視窗沒有太多內容，因為您還未實作`WndProc`函式。 換句話說，應用程式還不處理 Windows 現在會將傳送給它的訊息。

1. 若要處理訊息，我們會先新增訊息迴圈，以接聽訊息，Windows 會傳送。 當應用程式收到訊息時，這個迴圈會分派到您`WndProc`函式來處理。 此訊息迴圈會類似下列程式碼。

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   如需訊息迴圈中之結構和函式的詳細資訊，請參閱 [MSG](/windows/desktop/api/winuser/ns-winuser-msg)、 [GetMessage](/windows/desktop/api/winuser/nf-winuser-getmessage)、 [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)和 [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage)。

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

   是一個重要的訊息，以處理[WM_PAINT](/windows/desktop/gdi/wm-paint)訊息。 應用程式收到`WM_PAINT`必須更新時顯示的視窗部分的訊息。 當使用者移動程式視窗中，前面的視窗，然後將它移開一次，並不知道您的應用程式，這些事件發生時，就會發生的事件。 只有 Windows 知道，因此它會通知您`WM_PAINT`。 當第一次顯示視窗時，全都必須更新。

   若要處理 `WM_PAINT` 訊息，請先呼叫 [BeginPaint](/windows/desktop/api/winuser/nf-winuser-beginpaint)，然後處理用以配置視窗中文字、按鈕和其他控制項的所有邏輯，再呼叫 [EndPaint](/windows/desktop/api/winuser/nf-winuser-endpaint)。 應用程式，在開頭呼叫與結尾呼叫之間的邏輯是顯示字串"Hello，Windows desktop"！ 在視窗中顯示 "Hello, World!" 字串。 請注意，下列程式碼使用 [TextOut](/windows/desktop/api/wingdi/nf-wingdi-textouta) 函式來顯示字串。

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

   `HDC` 在程式碼是裝置內容，也就是 Windows 使用，讓您與圖形子系統進行通訊的應用程式的資料結構的控制代碼。 `BeginPaint`和`EndPaint`函式讓應用程式表現良好的公民，但未使用的裝置內容，還要長。 函式有助於讓圖形子系統可供其他應用程式使用。

1. 應用程式通常會處理許多其他訊息，例如[WM_CREATE](/windows/desktop/winmsg/wm-create)時第一次建立視窗，並[WM_DESTROY](/windows/desktop/winmsg/wm-destroy)視窗關閉時。 下列程式碼會顯示基本但完整的 `WndProc` 函式。

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

就如承諾一樣，以下是可用的應用程式的完整程式碼。

### <a name="to-build-this-example"></a>建立這個範例

1. 刪除任何您輸入的程式碼*HelloWindowsDesktop.cpp*在編輯器中。 複製此範例程式碼並貼到*HelloWindowsDesktop.cpp*:

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

1. 若要執行的應用程式，請按**F5**。 視窗，其中包含文字"Hello，Windows desktop"！ 應該會出現在顯示畫面的左上角。

   ![執行 DesktopApp 專案](../build/media/desktop-app-project-run-157.png "執行 DesktopApp 專案")

恭喜您！ 當您完成本逐步解說，並建置傳統 Windows 桌面應用程式。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)