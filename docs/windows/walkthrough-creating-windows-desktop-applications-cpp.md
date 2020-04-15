---
title: 演練:建立傳統的 Windows 桌面應用程式(C++)
description: 如何使用 Visual Studio、C++ 和 Win32 API 建立最小的傳統 Windows 桌面應用程式
ms.custom: get-started-article
ms.date: 11/03/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: da74778e79a08dd3ed2b5be0675981425264bdc0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351842"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>演練:建立傳統的 Windows 桌面應用程式(C++)

本演練演示如何在 Visual Studio 中創建傳統的 Windows 桌面應用程式。 您將建立的範例應用程式使用 Windows API 顯示「你好,Windows 桌面! 視窗中顯示 "Hello, World!" 的基本 Windows 傳統型應用程式。 您可以使用在這個逐步解說中開發的程式碼作為模式，來建立其他 Windows 傳統型應用程式。

Windows API(也稱為 Win32 API、Windows 桌面 API 和 Windows 經典 API)是一個基於 C 語言的框架,用於創建 Windows 應用程式。 它自 20 世紀 80 年代以來一直存在,數十年來一直用於創建 Windows 應用程式。 在 Windows API 之上建構了更進階、更易於程式設計的框架。 例如,MFC、ATL、.NET 框架。 即使是用 C++/WinRT 編寫的 UWP 和應用商店應用的最現代 Windows 運行時代碼也使用下面的 Windows API。 有關 Windows API 的詳細資訊,請參閱[Windows API 索引](/windows/win32/apiindex/windows-api-list)。 創建 Windows 應用程式的方法有很多種,但上述過程是第一個。

> [!IMPORTANT]
> 為了簡潔起見,文本中省略了一些代碼語句。 本文件末尾[的"生成代碼](#build-the-code)"部分顯示完整代碼。

## <a name="prerequisites"></a>Prerequisites

- 執行 Microsoft Windows 7 或更新版本的電腦。 建議使用 Windows 10 以獲得最佳開發體驗。

- Visual Studio 的複本。 如需如何下載並安裝 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。 當您執行安裝程式時，請確認已選取**使用 C++ 的桌面開發**工作負載。 如果您在安裝 Visual Studio 時未安裝此工作負載，也不用擔心。 您可以再次執行安裝程式並立即安裝。

   ![使用 C++ 的桌面開發](../build/media/desktop-development-with-cpp.png "使用 C++ 的桌面開發")

- 了解使用 Visual Studio IDE 的基本概念。 如果您先前使用過 Windows 傳統型應用程式，您應能輕鬆跟上。 如需簡介，請參閱 [Visual Studio IDE 功能導覽](/visualstudio/ide/visual-studio-ide)。

- 了解足夠的 C++ 語言基本概念。 別擔心，我們不會進行太複雜的操作。

## <a name="create-a-windows-desktop-project"></a>建立 Windows 桌面專案

按照以下步驟創建第一個 Windows 桌面專案。 走後,您將輸入工作中的 Windows 桌面應用程式的代碼。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>在 Visual Studio 2019 建立 Windows 桌面專案

1. 從主功能表，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話框的頂部,將 **「語言**」設定為**C++,** 將**平台**設定為**Windows,** 並將**專案類型**設定為**桌面**。

1. 從篩選的項目類型清單中,選擇 Windows**桌面精靈**,然後選擇 **「下一步**」 。 在下一頁中,輸入項目的名稱,例如*DesktopApp*。

1. 選擇 [建立] **** 按鈕以建立專案。

1. 現在將顯示 **「Windows 桌面項目**」對話框。 在 **「應用程式類型**」下,選擇**桌面應用程式 (.exe)。** 在 [其他選項] **** 下，選取 [空專案] ****。 選擇 **「確定」** 以建立專案。

1. 在**解決方案資源管理器**中,右鍵單擊**桌面應用**專案,選擇 **「添加**」,然後選擇 **「新專案**」。

   ![新增新專案加入到桌面應用程式專案](../build/media/desktop-app-project-add-new-item-153.gif "新增新專案加入到桌面應用程式專案")

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。 在 **「名稱」** 方塊中,鍵入檔案的名稱,例如*HelloWindowsDesktop.cpp*。 選擇 **「添加**」 。

   ![新增 .cpp 檔案加入桌面套用專案](../build/media/desktop-app-add-cpp-file-153.png "新增 .cpp 檔案加入桌面套用專案")

現在,您的項目已創建,源檔在編輯器中打開。 要繼續,請向前跳過以[建立代碼](#create-the-code)。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>在 Visual Studio 2017 建立 Windows 桌面專案

1. 在 [檔案]**** 功能表上，選擇 [新增]**** 然後選擇 [專案]****。

1. 在新**項目**對話框中,在左窗格中展開 **「已安裝** > **的視覺C++」,** 然後選擇**Windows 桌面**。 在中間窗格中,選擇**Windows 桌面精靈**。

   在 **「名稱」** 方塊中,鍵入項目的名稱,例如*DesktopApp*。 選擇 **"確定**"。

   ![命名桌面應用程式專案](../build/media/desktop-app-new-project-name-153.png "命名桌面應用程式專案")

1. 在 **「Windows 桌面項目」** 對話方塊中,在 **「應用程式類型**」下,選擇**Windows 應用程式 (.exe)。** 在 [其他選項] **** 下，選取 [空專案] ****。 決定未選擇**預先選擇 。** 選擇 **「確定」** 以建立專案。

1. 在**解決方案資源管理器**中,右鍵單擊**桌面應用**專案,選擇 **「添加**」,然後選擇 **「新專案**」。

   ![新增新專案加入到桌面應用程式專案](../build/media/desktop-app-project-add-new-item-153.gif "新增新專案加入到桌面應用程式專案")

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。 在 **「名稱」** 方塊中,鍵入檔案的名稱,例如*HelloWindowsDesktop.cpp*。 選擇 **「添加**」 。

   ![新增 .cpp 檔案加入桌面套用專案](../build/media/desktop-app-add-cpp-file-153.png "新增 .cpp 檔案加入桌面套用專案")

現在,您的項目已創建,源檔在編輯器中打開。 要繼續,請向前跳過以[建立代碼](#create-the-code)。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>在 Visual Studio 2015 建立 Windows 桌面專案

1. 在 [檔案]**** 功能表上，選擇 [新增]**** 然後選擇 [專案]****。

1. 在新**項目**對話框中,在左窗格中,展開 **「已安裝** > **樣本** > **」可視化C++,** 然後選擇**Win32**。 在中間窗格選取 [Win32 專案] ****。

   在 **「名稱」** 方塊中,鍵入項目的名稱,例如*DesktopApp*。 選擇 **"確定**"。

   ![命名桌面應用程式專案](../build/media/desktop-app-new-project-name-150.png "命名桌面應用程式專案")

1. 在**Win32 應用程式精靈**的**概述**頁上,選擇 **「下一步**」。

   ![在 Win32 應用程式精靈概述中建立桌面應用程式](../build/media/desktop-app-win32-wizard-overview-150.png "在 Win32 應用程式精靈概述中建立桌面應用程式")

1. 在**應用程式應用程式設定「** 設定」 頁上,在 **「應用程式類型」** 下,選擇 Windows**應用程式**。 在 **「其他選項**」下,取消選中**預編譯標頭**,然後選擇 **「空專案**」。 選擇 **「完成」** 以建立專案。

1. 在**解決方案資源管理器**中,右鍵單擊桌面應用專案,選擇 **「添加**」,然後選擇 **「新專案**」。

   ![新增新專案加入到桌面應用程式專案](../build/media/desktop-app-project-add-new-item-150.gif "新增新專案加入到桌面應用程式專案")

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。 在 **「名稱」** 方塊中,鍵入檔案的名稱,例如*HelloWindowsDesktop.cpp*。 選擇 **「添加**」 。

   ![新增 .cpp 檔案加入桌面套用專案](../build/media/desktop-app-add-cpp-file-150.png "新增 .cpp 檔案加入桌面套用專案")

現在,您的項目已創建,源檔在編輯器中打開。

::: moniker-end

## <a name="create-the-code"></a>建立代碼

接下來,您將學習如何在 Visual Studio 中為 Windows 桌面應用程式創建代碼。

### <a name="to-start-a-windows-desktop-application"></a>啟動 Windows 傳統型應用程式

1. 正如每個 C 應用程式和 C++ 應用程式`main`都必須具有函數作為起點一樣`WinMain`,每個 Windows 桌面 應用程式都必須具有一個函數。 `WinMain` 具有下列語法。

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   有關此函數的參數和傳回值的資訊,請參閱[WinMain 入口點](/windows/win32/api/winbase/nf-winbase-winmain)。

   > [!NOTE]
   > 所有這些額外的單詞,如`CALLBACK`或`HINSTANCE`,`_In_`或 ? 傳統的 Windows API 廣泛使用 typedef 和預處理器宏來抽象類型和特定於平台的代碼的一些詳細資訊,例如調用約定 **、__declspec**聲明和編譯器雜注。 在可視化工作室中,您可以使用"IntelliSense[快速資訊](/visualstudio/ide/using-intellisense#quick-info)"功能查看這些類型定義和宏定義的內容。 將滑鼠懸停在感興趣的字上,或選擇它,然後按**Ctrl**+**K** **、Ctrl**+**I,** 查看包含定義的小彈出視窗。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。 參數和返回類型通常使用*SAL 註釋*來説明捕獲程式設計錯誤。 有關詳細資訊,請參閱使用[SAL 註解來減少 C/C++代碼缺陷](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)。

1. Windows 桌面&lt;程式 需要 windows.h>。 &lt;tchar.h`TCHAR`>定义 宏,如果項目中定義了 UNICODE 符號,則宏最終解析為**wchar_t,** 否則它將解析為**char**。  如果您始終啟用啟用 UNICODE 構建,則不需要 TCHAR,只需直接使用**wchar_t**即可。

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. 除了該功能`WinMain`外,每個 Windows 桌面應用程式還必須具有視窗過程功能。 此函數通常命名為`WndProc`,但您可以隨心所欲地命名它。 `WndProc` 具有下列語法。

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   此函數中,編寫程式程式在發生*事件*時從 Windows 接收*的消息*。 例如,如果使用者在應用程式中選擇"確定"按鈕,Windows 會向您發送消息,您`WndProc`可以在函數內編寫代碼,執行任何適當的操作。 這稱為*處理*事件。 您只處理與應用程式相關的事件。

   如需詳細資訊，請參閱 [Window 程序](/windows/win32/winmsg/window-procedures)。

### <a name="to-add-functionality-to-the-winmain-function"></a>將功能加入 WinMain 函式中

1. 在`WinMain`函數中,填充[類型為 WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw)的結構。 結構包含有關視窗的資訊:應用程式圖示、視窗的背景顏色、要在標題列中顯示的名稱等。 重要的是,它包含指向視窗過程的函數指標。 下列範例會顯示一個典型的 `WNDCLASSEX` 結構。

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

   有關上述結構欄位的資訊,請參閱[WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw)。

1. 向`WNDCLASSEX`Windows 註冊 ,以便瞭解視窗以及如何向視窗發送訊息。 請使用 [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) 函式，並將視窗類別結構當做引數傳遞。 使用`_T`巨集是因為我們`TCHAR`使用類型 。

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

   此函數返回`HWND`一個 ,它是視窗的句柄。 句柄有點像 Windows 用來跟蹤打開的視窗的指標。 如需詳細資訊，請參閱 [Windows 資料類型](/windows/win32/WinProg/windows-data-types)。

1. 此時,視窗已創建,但我們仍然需要告訴 Windows 使其可見。 這就是此程式碼的作用:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   顯示的視窗沒有太多內容,因為您尚未實現該`WndProc`函數。 換句話說,應用程式尚未處理 Windows 現在發送給它的消息。

1. 要處理這些消息,我們首先添加一個消息循環來偵聽 Windows 發送的消息。 當應用程式收到消息時,此迴圈會將其調度到要處理的`WndProc`函數。 此訊息迴圈會類似下列程式碼。

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

   要處理的一條重要資訊是[WM_PAINT](/windows/win32/gdi/wm-paint)消息。 當必須更新其顯示`WM_PAINT`視窗的一部分時,應用程式將接收消息。 當使用者在視窗前面移動視窗,然後再次將其移開時,可能會發生此事件。 您的應用程式不知道這些事件何時發生。 只有 Windows 知道,因此它會`WM_PAINT`通過消息 通知你的應用。 首次顯示視窗時,必須更新所有視窗。

   若要處理 `WM_PAINT` 訊息，請先呼叫 [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint)，然後處理用以配置視窗中文字、按鈕和其他控制項的所有邏輯，再呼叫 [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint)。 對於應用程式,開始調用和結束呼叫之間的邏輯是顯示字串「你好,Windows 桌面! 在視窗中顯示 "Hello, World!" 字串。 請注意，下列程式碼使用 [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) 函式來顯示字串。

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

   `HDC`代碼中是設備上下文的句柄,這是 Windows 用於使應用程式與圖形子系統通訊的數據結構。 `BeginPaint`和`EndPaint`函數使應用程式像好公民一樣運行,並且使用設備上下文的時間不會超過其需要的時間。 這些功能有助於使圖形子系統可供其他應用程式使用。

1. 應用程式通常處理許多其他消息。 例如,在首次創建視窗時[WM_CREATE,](/windows/win32/winmsg/wm-create)並在關閉視窗時[WM_DESTROY。](/windows/win32/winmsg/wm-destroy) 下列程式碼會顯示基本但完整的 `WndProc` 函式。

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

正如所承諾的,下面是工作應用程式的完整代碼。

### <a name="to-build-this-example"></a>建立這個範例

1. 刪除您在*HelloWindowsDesktop.cpp*中輸入的任何代碼。 複製此範例代碼,然後將其貼上到*HelloWindowsDesktop.cpp:*

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

1. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。 編譯結果應顯示在可視化工作室的 **「輸出」** 視窗中。

   ![編譯桌面應用程式專案](../build/media/desktop-app-project-build-150.gif "編譯桌面應用程式專案")

1. 若要執行應用程式，請按 **F5**。 包含文字「你好,Windows 桌面! 應該會出現在顯示畫面的左上角。

   ![執行桌面應用程式專案](../build/media/desktop-app-project-run-157.PNG "執行桌面應用程式專案")

恭喜！ 您已完成本演練並建構了傳統的 Windows 桌面應用程式。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)
