---
title: Dll 和 Visual C++執行時間程式庫行為
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
ms.openlocfilehash: 572a0ba70c1ba2d46d2d9fd6d8ac543a77bbbc01
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417310"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Dll 和 Visual C++執行時間程式庫行為

當您使用 Visual Studio 建立動態連結程式庫（DLL）時，連結器預設會包含 [Visual C++執行時間程式庫（VCRuntime）]。 VCRuntime 包含初始化和終止 C/C++可執行檔所需的程式碼。 當連結到 DLL 時，VCRuntime 程式碼會提供一個 `_DllMainCRTStartup` 稱為的內部 DLL 進入點函式，它會處理 Windows OS 訊息至 DLL，以附加至進程或執行緒。 `_DllMainCRTStartup` 函式會執行基本工作，例如堆疊緩衝區安全性設定、C 執行時間程式庫（CRT）初始化和終止，以及呼叫靜態和全域物件的函式和析構函數。 `_DllMainCRTStartup` 也會呼叫其他程式庫（例如 WinRT、MFC 和 ATL）的攔截函式，以執行自己的初始化和終止。 如果沒有此初始化，CRT 和其他程式庫以及您的靜態變數都會保留為未初始化的狀態。 無論您的 DLL 使用靜態連結的 CRT 或動態連結的 CRT DLL，都會呼叫相同的 VCRuntime 內部初始化和終止常式。

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>預設 DLL 進入點 _DllMainCRTStartup

在 Windows 中，所有 Dll 都可以包含選擇性的進入點函式，通常稱為 `DllMain`，會同時呼叫以進行初始化和終止。 這讓您有機會視需要配置或釋放額外的資源。 Windows 會在四種情況下呼叫進入點函式：進程附加、進程卸離、執行緒附加和執行緒卸離。 當 DLL 載入至進程位址空間時（不論是載入使用它的應用程式），或應用程式在執行時間要求 DLL 時，作業系統會建立個別的 DLL 資料複本。 這稱為「*進程附加*」。 當載入 DLL 的進程建立新的執行緒時，就會發生*執行緒附加*。 執行緒中斷時就會發生*執行緒卸離*，而*進程卸離*則是在不再需要 DLL，而是由應用程式釋放時。 作業系統會個別呼叫每個事件的 DLL 進入點，並傳遞每個事件種類的*reason*引數。 例如，OS 會將 `DLL_PROCESS_ATTACH` 做為*reason*引數傳送到信號處理常式附加。

VCRuntime 程式庫會提供稱為 `_DllMainCRTStartup` 的進入點函式，以處理預設的初始化和終止作業。 在進程附加上，`_DllMainCRTStartup` 函式會設定緩衝區安全性檢查、初始化 CRT 和其他程式庫、初始化執行時間類型資訊、初始化和呼叫靜態和非本機資料的函式、初始化執行緒區域儲存區、遞增每個附加的內部靜態計數器，然後呼叫使用者或程式庫提供的 `DllMain`。 在進程卸離時，函式會反向執行這些步驟。 它會呼叫 `DllMain`、遞減內部計數器、呼叫析構函式、呼叫 CRT 終止函式和已註冊的 `atexit` 函式，以及通知任何其他終止的程式庫。 當附件計數器變成零時，函式會傳回 `FALSE` 以向 Windows 表示 DLL 可以卸載。 線上程附加和執行緒卸離期間，也會呼叫 `_DllMainCRTStartup` 函式。 在這些情況下，VCRuntime 程式碼本身不會執行任何額外的初始化或終止，而只會呼叫 `DllMain` 來傳遞訊息。 如果 `DllMain` 從進程附加、信號失敗中傳回 `FALSE`，`_DllMainCRTStartup` 再次呼叫 `DllMain` 並將 `DLL_PROCESS_DETACH` 做為*reason*引數，則會進行終止進程的其餘部分。

在 Visual Studio 中建立 Dll 時，VCRuntime 所提供的預設進入點 `_DllMainCRTStartup` 會自動連結在中。 您不需要使用[/ENTRY （進入點符號）](reference/entry-entry-point-symbol.md)連結器選項來指定 DLL 的進入點函式。

> [!NOTE]
> 雖然您可以使用/ENTRY：連結器選項來指定 DLL 的另一個進入點函式，但我們並不建議這麼做，因為您的進入點函式必須以相同的順序複製 `_DllMainCRTStartup` 執行的所有專案。 VCRuntime 提供可讓您複製其行為的函式。 例如，您可以立即在進程附加上呼叫[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) ，以支援[/gs （緩衝區安全性檢查）](reference/gs-buffer-security-check.md)緩衝區檢查選項。 您可以呼叫 `_CRT_INIT` 函式，傳遞與進入點函式相同的參數，以執行 DLL 初始化或終止函式的其餘部分。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>初始化 DLL

您的 DLL 可能會有初始化程式碼，必須在您的 DLL 載入時執行。 為了讓您執行自己的 DLL 初始化和終止函式，`_DllMainCRTStartup` 會呼叫稱為 `DllMain` 的函式，您可以提供此函式。 您的 `DllMain` 必須具有 DLL 進入點所需的簽章。 預設的進入點函式 `_DllMainCRTStartup` 會使用 Windows 所傳遞的相同參數來呼叫 `DllMain`。 根據預設，如果您未提供 `DllMain` 函式，Visual Studio 會為您提供一個，並將它連結在中，`_DllMainCRTStartup` 一律會有要呼叫的專案。 這表示，如果您不需要初始化 DLL，則在建立 DLL 時，不會有任何特殊的條件。

這是用於 `DllMain`的簽章：

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

某些程式庫會為您包裝 `DllMain` 函式。 例如，在一般的 MFC DLL 中，執行 `CWinApp` 物件的 `InitInstance` 和 `ExitInstance` 成員函式，以執行 DLL 所需的初始化和終止。 如需詳細資訊，請參閱[初始化標準 MFC dll](#initializing-regular-dlls)一節。

> [!WARNING]
> 您可以在 DLL 進入點中安全地執行的動作有很大的限制。 請參閱 `DllMain`中不安全呼叫之特定 Windows Api 的[一般最佳做法](/windows/win32/Dlls/dynamic-link-library-best-practices)。 如果您需要任何專案，但最簡單的初始化則會在 DLL 的初始化函式中執行該作業。 您可以要求應用程式在執行 `DllMain` 之後，以及呼叫 DLL 中的任何其他函式之後，呼叫初始化函式。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化一般（非 MFC） Dll

若要在使用 VCRuntime 提供之 `_DllMainCRTStartup` 進入點的一般（非 MFC） Dll 中執行自己的初始化，您的 DLL 原始程式碼必須包含稱為 `DllMain`的函式。 下列程式碼提供基本的基礎架構，其中顯示 `DllMain` 的定義可能會如下所示：

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
> 舊版 Windows SDK 檔指出必須在連結器命令列上，使用/ENTRY 選項來指定 DLL 進入點函式的實際名稱。 使用 Visual Studio 時，如果您的進入點函式名稱為 `DllMain`，則不需要使用/ENTRY 選項。 事實上，如果您使用/ENTRY 選項，並將您的進入點函式命名為 `DllMain`以外的專案，則 CRT 不會正確地初始化，除非您的進入點函式會進行 `_DllMainCRTStartup` 所進行的相同初始化呼叫。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>初始化一般 MFC Dll

因為標準的 MFC Dll 具有 `CWinApp` 物件，所以它們應該在與 MFC 應用程式相同的位置中執行其初始化和終止工作：在 DLL 的 `CWinApp`衍生類別的 `InitInstance` 和 `ExitInstance` 成員函式中。 因為 MFC 提供 `DLL_PROCESS_ATTACH` 和 `DLL_PROCESS_DETACH``_DllMainCRTStartup` 所呼叫的 `DllMain` 函式，所以您不應該撰寫自己的 `DllMain` 函數。 MFC 提供的 `DllMain` 函式會在載入 DLL 時呼叫 `InitInstance`，並在卸載 DLL 之前呼叫 `ExitInstance`。

一般 MFC DLL 可以藉由在其 `InitInstance` 函式中呼叫[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)和[TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) ，來追蹤多個執行緒。 這些函數可讓 DLL 追蹤執行緒特定的資料。

在動態連結至 MFC 的一般 MFC DLL 中，如果您使用任何 MFC OLE、MFC 資料庫（或 DAO），或分別是 MFC 通訊端支援，debug MFC 延伸 Dll MFCO*版本*d. .DLL、MFCD*版本*d. .Dll 和 MFCN*版本*d. .dll （其中*version*是版本號碼）會自動連結在一起。 您必須針對您在一般 MFC DLL 的 `CWinApp::InitInstance`中使用的每個 Dll，呼叫下列其中一個預先定義的初始化函數。

|MFC 支援的類型|要呼叫的初始化函數|
|-------------------------|-------------------------------------|
|MFC OLE （MFCO*版本*d. .dll）|`AfxOleInitModule`|
|MFC 資料庫（MFCD*版本*d. .dll）|`AfxDbInitModule`|
|MFC 通訊端（MFCN*版本*d. .dll）|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 延伸 Dll

因為 MFC 延伸 Dll 沒有 `CWinApp`衍生的物件（如同一般的 MFC Dll），所以您應該將初始化和終止程式碼加入至 MFC DLL Wizard 所產生的 `DllMain` 函式中。

此 wizard 提供 MFC 延伸 Dll 的下列程式碼。 在程式碼中，`PROJNAME` 是專案名稱的預留位置。

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

在初始化期間建立新的 `CDynLinkLibrary` 物件，可讓 MFC 延伸模組 DLL 將 `CRuntimeClass` 物件或資源匯出至用戶端應用程式。

如果您要從一個或多個一般 MFC Dll 使用 MFC 延伸模組 DLL，您必須匯出建立 `CDynLinkLibrary` 物件的初始化函數。 該函式必須從使用 MFC 延伸 DLL 的每個標準 MFC Dll 呼叫。 呼叫這個初始化函式的適當位置，是在使用任何 MFC 延伸 DLL 的匯出類別或函式之前，在一般 MFC DLL 的 `CWinApp`衍生物件的 `InitInstance` 成員函式中。

在 MFC DLL Wizard 產生的 `DllMain` 中，`AfxInitExtensionModule` 的呼叫會在建立 `CDynLinkLibrary` 物件時，捕捉模組的執行時間類別（`CRuntimeClass` 結構）以及其物件 factory （`COleObjectFactory` 物件）以供使用。 您應該檢查 `AfxInitExtensionModule`的傳回值。如果從 `AfxInitExtensionModule`傳回零值，則會從您的 `DllMain` 函式傳回零。

如果您的 MFC 延伸 DLL 將明確連結至可執行檔（表示可執行檔呼叫 `AfxLoadLibrary` 以連結至 DLL），您應該在 `DLL_PROCESS_DETACH`上加入 `AfxTermExtensionModule` 的呼叫。 當每個進程從 MFC 延伸模組 DLL 卸離時，此函式可讓 MFC 清除 MFC 延伸模組 dll （這會在進程結束時發生，或因 `AfxFreeLibrary` 呼叫而卸載 DLL 時）。 如果您的 MFC 擴充 DLL 會隱含地連結至應用程式，則不需要呼叫 `AfxTermExtensionModule`。

當釋放 DLL 時，明確連結至 MFC 擴充 Dll 的應用程式必須呼叫 `AfxTermExtensionModule`。 如果應用程式使用多個執行緒，它們也應該使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` （而不是 Win32 函數 `LoadLibrary` 和 `FreeLibrary`）。 使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 可確保在載入和卸載 MFC 延伸模組 DLL 時執行的啟動和關閉程式碼不會損毀全域 MFC 狀態。

由於 MFCx0 會在呼叫 `DllMain` 時完全初始化，因此您可以在 `DllMain` 中配置記憶體和呼叫 MFC 函式（不同于 MFC 的16位版本）。

擴充 Dll 可以處理 `DllMain` 函式中的 `DLL_THREAD_ATTACH` 和 `DLL_THREAD_DETACH` 案例，藉此負責多執行緒。 當執行緒附加和卸離 DLL 時，這些案例會傳遞給 `DllMain`。 當 DLL 附加時呼叫[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) ，可讓 dll 針對附加至 dll 的每個執行緒維護執行緒區域儲存區（TLS）索引。

請注意，標頭檔 Afxdllx 包含 MFC 延伸 Dll 中使用之結構的特殊定義，例如 `AFX_EXTENSION_MODULE` 和 `CDynLinkLibrary`的定義。 您應該在 MFC 延伸模組 DLL 中包含此標頭檔。

> [!NOTE]
>  請務必不要在*pch* （Visual Studio 2017 和更早版本的*stdafx.h* ）中定義或取消指定任何 `_AFX_NO_XXX` 宏。 這些宏僅適用于檢查特定目標平臺是否支援該功能的目的。 您可以撰寫程式來檢查這些宏（例如 `#ifndef _AFX_NO_OLE_SUPPORT`），但您的程式絕對不應定義或取消定義這些宏。

在 Windows SDK 的[動態連結程式庫中使用執行緒區域儲存區](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)中包含處理多執行緒處理的範例初始化函式。 請注意，此範例包含稱為 `LibMain`的進入點函式，但您應該將此函式命名為 `DllMain`，使其適用于 MFC 和 C 執行時間程式庫。

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)<br/>
[DllMain 進入點](/windows/win32/Dlls/dllmain)<br/>
[動態連結程式庫的最佳做法](/windows/win32/Dlls/dynamic-link-library-best-practices)
