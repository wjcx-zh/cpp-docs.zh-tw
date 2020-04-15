---
title: DLL 和 Visual C++ 執行階段程式庫行為
ms.date: 08/19/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
ms.openlocfilehash: 2f2ffb13e6a80b144298bbf8cd76b5666a10b4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335668"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLL 和 Visual C++ 執行階段程式庫行為

預設情況下,使用 Visual Studio 構建動態連結庫 (DLL) 時,連結器包括可視C++運行時庫 (VCRuntime)。 VCRuntime 包含初始化和終止 C/C++可執行檔所需的代碼。 當連結到 DLL 時,VCRuntime 程式碼提供一個`_DllMainCRTStartup`內部 DLL 入口點函數,該函數調用該函數處理 Windows OS 訊息到 DLL 以附加到行程或線程或從行程或線程分離。 該`_DllMainCRTStartup`函數執行基本任務,如堆疊緩衝區安全設置、C 運行時庫 (CRT) 初始化和終止,以及對靜態和全域物件的構造函數和析構函數的調用。 `_DllMainCRTStartup`還調用其他庫(如 WinRT、MFC 和 ATL)的掛鉤函數來執行自己的初始化和終止。 如果沒有此初始化,CRT 和其他庫以及靜態變數將處於未初始化狀態。 無論您的 DLL 使用靜態連結的 CRT 還是動態連結的 CRT DLL,都呼叫相同的 VCRuntime 內部初始化和終止例程。

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>預設 DLL 入口點_DllMainCRTStartup

在 Windows 中,所有 DLL 都可以包含一個`DllMain`可選的入口 點函數,通常稱為 ,該函數同時調用初始化和終止。 這使您有機會根據需要分配或釋放其他資源。 Windows 在四種情況下調用入口點功能:進程附加、進程分離、線程連接和線程分離。 當 DLL 載入到行程位址空間時,或者在載入使用它的應用程式時,或者當應用程式在執行時請求 DLL 時,作業系統將創建 DLL 資料的單獨副本。 這稱為*行程附加*。 當 DLL 載入的過程建立新線程時,將發生*線程附加*。 *線程分離*線上程終止時發生,*行程分離*是不再需要 DLL 並由應用程式釋放時發生的。 操作系統對每個事件分別調用 DLL 入口點,傳遞每個事件類型的*推理*參數。 例如,操作系統作為*原因*參數`DLL_PROCESS_ATTACH`發送到信號進程附加。

VCRuntime 函式庫提供一個入口點`_DllMainCRTStartup`函數, 用於處理預設初始化和終止操作。 在行程附加時,`_DllMainCRTStartup`函數設定緩衝區安全檢查,初始化 CRT 和其他函式庫,初始化執行時類型資訊,初始化和呼叫靜態和非本地資料的建構函數,初始化線程本地儲存,為每個附加增加內部靜態計數器,然後呼`DllMain`叫使用者或函式庫提供的 。 在進程分離時,函數將反向執行這些步驟。 它調用`DllMain`,遞減內部計數器,調用析構函數,調用CRT終止函數和`atexit`註冊 函數,並通知任何其他庫的終止。 當附件計數器為零時,函數將返回`FALSE`以向 Windows 指示可以卸載 DLL。 在`_DllMainCRTStartup`線程連接和線程分離期間,還會調用該函數。 在這些情況下,VCRuntime 代碼本身不會執行額外的初始化或終止,只是調`DllMain`用傳遞消息。 如果`DllMain``FALSE`從行程附加返回、發出信號失敗`_DllMainCRTStartup`、`DllMain`再次調用`DLL_PROCESS_DETACH`並作為*原因*參數傳遞,則通過終止過程的其餘部分。

在 Visual Studio 中`_DllMainCRTStartup`建構 DLL 時,VCRuntime 提供的預設入口點將自動連結在其中。 無需使用[/ENTRY(入口點符號)](reference/entry-entry-point-symbol.md)連結器選項為 DLL 指定入口點函數。

> [!NOTE]
> 雖然可以使用 /ENTRY: 連結器選項為 DLL 指定另一個入口點函數,但我們不推薦它,因為入口點函數必須按相同的`_DllMainCRTStartup`順序複製所有 執行該功能的功能。 VCRuntime 提供允許您複製其行為的函數。 例如,您可以在行程附加時立即調用[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)以支援[/GS(緩衝區安全檢查)](reference/gs-buffer-security-check.md)緩衝區檢查選項。 您可以調用`_CRT_INIT`函數,傳遞與入口點函數相同的參數,以執行 DLL 初始化或終止函數的其餘部分。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>初始化 DLL

您的 DLL 可能具有初始化代碼,這些代碼必須在載入 DLL 時執行。 為了執行自己的 DLL 初始化和終止函`_DllMainCRTStartup`數, 呼叫一個可以提供的`DllMain`函數。 您必須`DllMain`具有 DLL 入口點所需的簽名。 默認入口點函數`_DllMainCRTStartup``DllMain`使用 Windows 傳遞的相同參數調用。 預設情況下,如果您不提供函數,Visual `DllMain` Studio 會為您提供一個函數並將其連結在`_DllMainCRTStartup`其中, 以便始終具有可調用的內容。 這意味著,如果您不需要初始化 DLL,則構建 DLL 時無需執行任何特別操作。

這是用來簽署的`DllMain`簽章 :

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

某些函式庫為您包裝`DllMain`函數 。 例如,在常規 MFC DLL`CWinApp`中,`InitInstance``ExitInstance`實現物件的和成員函數,以執行 DLL 所需的初始化和終止。 有關詳細資訊,請參閱[初始化常規 MFC DLL](#initializing-regular-dlls)部分。

> [!WARNING]
> 在 DLL 入口點中可以安全地執行哪些操作有顯著限制。 有關不安全的特定 Windows API,`DllMain`請參考[一般最佳做法](/windows/win32/Dlls/dynamic-link-library-best-practices)。 如果您需要任何內容,但最簡單的初始化,然後在 DLL 的初始化函數中執行此操作。 您可以要求應用程式在執行後`DllMain`和在 DLL 中調用任何其他函數之前調用初始化函數。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化一般(非 MFC) DLL

要在使用 VCRuntime`_DllMainCRTStartup`提供的入口點的普通(非 MFC) DLL 中執行自己的初始化,DLL`DllMain`原始程式碼必須包含名為的函數。 以下代碼提供了一個基本骨架,顯示其`DllMain`定義可能是什麼樣子:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason)
    {
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```

> [!NOTE]
> 較舊的 Windows SDK 文件指出,必須在帶有 /ENTRY 選項的連結器命令列上指定 DLL 入口點函數的實際名稱。 使用 Visual Studio,如果入口點函數的`DllMain`名稱為 ,則無需使用 /ENTRY 選項。 事實上,如果您使用 /ENTRY 選項並命名入口點函數`DllMain`,則 CRT 不會正確初始化,除非您的`_DllMainCRTStartup`入口點函數 發出相同的初始化調用。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>初始化一般 MFC DLL

由於常規 MFC`CWinApp`DLL 具有物件,因此它們應在與 MFC 應用程式相同的位置執行初始化`InitInstance`和終止`ExitInstance``CWinApp`任務:在 DLL 派生類的 和成員函數中。 `DllMain`因為 MFC`_DllMainCRTStartup``DLL_PROCESS_ATTACH`提供`DLL_PROCESS_DETACH`由和調用的函數,因此不應`DllMain`編寫自己的 函數。 在載入`DllMain`DLL`InitInstance`並在卸載 DLL`ExitInstance`之前呼叫 MFC 提供的函數調用。

常規 MFC DLL`InitInstance`可以通過在其 函數中調用[TlsAlloc 和 TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)來追蹤多個線程。 [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) 這些函數允許 DLL 跟蹤特定於線程的數據。

在動態連結到 MFC 的常規 MFC DLL 中,如果您分別使用任何 MFC OLE、MFC 資料庫(或 DAO)或 MFC 插槽支援,則調試 MFC 擴展 DL MFCO*版本*D.dll、MFCD*版本*D.dll 和 MFCN*版本*D.dll(*其中版本*是版本號)將自動連結。 您必須為一般 MFC DLL 中正在使用的每個 DLL 呼叫以下預先定義`CWinApp::InitInstance`的初始化函數之一 。

|MFC 支援的類型|要呼叫的初始化函數|
|-------------------------|-------------------------------------|
|MFC OLE(MFCO*版本*D.dll)|`AfxOleInitModule`|
|MFC 資料庫(MFCD*版本*D.dll)|`AfxDbInitModule`|
|MFC 插座 (MFCN*版本*D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 延伸 DLL

由於 MFC 擴展`CWinApp`DLL 沒有派生物件(常規 MFC DLL 也相同),因此應將`DllMain`初始化和終止碼添加到 MFC DLL 嚮導生成的函數中。

該嚮導為 MFC 擴展 DLL 提供以下代碼。 在代碼中,`PROJNAME`是專案名稱的佔位符。

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
#include <afxdllx.h>

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      TRACE0("PROJNAME.DLL Initializing!\n");

      // MFC extension DLL one-time initialization
      AfxInitExtensionModule(PROJNAMEDLL,
                                 hInstance);

      // Insert this DLL into the resource chain
      new CDynLinkLibrary(Dll3DLL);
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      TRACE0("PROJNAME.DLL Terminating!\n");
   }
   return 1;   // ok
}
```

在初始化`CDynLinkLibrary`期間創建新物件允許 MFC`CRuntimeClass`擴展 DLL 將物件或資源匯出到用戶端應用程式。

如果要使用來自一個或多個常規 MFC DLL 的 MFC 擴展 DLL,則必須匯出創建`CDynLinkLibrary`物件的初始化函數。 該函數必須從使用 MFC 擴展 DLL 的每個常規 MFC DLL 中調用。 在使用任何 MFC 擴展`InitInstance`DLL 匯出的類或函數之前`CWinApp`,常規 MFC DLL 派生物件的成員函數中可以調用此初始化函數的適當位置。

在`DllMain`MFC DLL 精靈產生的中`AfxInitExtensionModule`,用於擷取模組的執行時`CRuntimeClass`類( 結構)及其`COleObjectFactory`物件工廠( 物件)的呼`CDynLinkLibrary`叫,用於創建物件時。 應檢查`AfxInitExtensionModule`的傳回值 。如果從`AfxInitExtensionModule`返回零值,則從`DllMain`返回函數返回零。

如果您的 MFC 分機 DLL 將顯式連結到可執行檔(表示`AfxLoadLibrary`可執行呼叫 連結到 DLL),則應向`AfxTermExtensionModule`上`DLL_PROCESS_DETACH`添加呼叫。 此功能允許 MFC 在每個行程從 MFC 分機 DLL 分離時清理 MFC 分機`AfxFreeLibrary`DLL(當行程退出或由於呼叫而卸載 DLL 時發生)。 如果您的 MFC 分機 DLL 會隱用的`AfxTermExtensionModule`應用程式,則不需要呼叫 。

顯式連結到 MFC 擴展 DLL`AfxTermExtensionModule`的應用程式在釋放 DLL 時必須調用。 如果應用程式使用多個`AfxLoadLibrary`線`AfxFreeLibrary`程 ,它們還應使用`LoadLibrary``FreeLibrary`和 (而不是 Win32 函數 和 )。 使用`AfxLoadLibrary``AfxFreeLibrary`並確保在載入和卸載 MFC 擴展 DLL 時執行的啟動和關閉代碼不會損壞全域 MFC 狀態。

由於 MFCx0.dll 在調`DllMain`用時 已完全初始化,因此`DllMain`您可以在其中 分配記憶體並調用 MFC 函數(與 16 位元版本的 MFC 不同)。

擴展 DLL`DLL_THREAD_ATTACH``DLL_THREAD_DETACH``DllMain`可以通過處理 函數中的 和案例來處理多線程。 `DllMain`當線程從 DLL 連接和分離時,這些情況將傳遞到。 在附加 DLL 時調用[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)允許 DLL 維護附加到 DLL 的每個線程的線程本地存儲 (TLS) 索引。

請注意,標頭檔 Afxdllx.h 包含 MFC 擴展 DLL 中使用的結構`AFX_EXTENSION_MODULE``CDynLinkLibrary`的特殊定義,例如和 的定義。 您應該在 MFC 副檔名 DLL 中包括此標頭檔。

> [!NOTE]
> 重要的是,您既不定義也不定義`_AFX_NO_XXX`*pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)* 中的任何宏。 這些宏的存在僅用於檢查特定目標平臺是否支援該功能。 可以編寫程式來檢查這些宏(例如`#ifndef _AFX_NO_OLE_SUPPORT`),但程式絕不應定義或取消定義這些宏。

處理多線程的範例初始化功能包含在 Windows SDK[中的動態連結庫中使用線程本地儲存](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)中。 請注意,該示例包含一個稱為`LibMain`的切入點函數,但應命名此函`DllMain`數 ,以便它適用於 MFC 和 C 運行時庫。

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)<br/>
[Dll 主入口點](/windows/win32/Dlls/dllmain)<br/>
[動態連結庫最佳實務](/windows/win32/Dlls/dynamic-link-library-best-practices)
