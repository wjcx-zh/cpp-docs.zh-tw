---
title: Dll 和 Visual c + + 執行階段程式庫行為
ms.date: 11/04/2016
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
ms.openlocfilehash: 084741a3a408fe79e27c3fab81e1f5c4c9f06c4e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414586"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Dll 和 Visual c + + 執行階段程式庫行為

當您建置動態連結程式庫 (DLL)，使用 Visual c + + 中，依預設時，連結器就會包含 Visual c + + 執行階段程式庫 (VCRuntime)。 VCRuntime 包含初始化及終止 C/c + + 可執行檔所需的程式碼。 當連結的 dll，VCRuntime 程式碼會提供內部 DLL 進入點函式呼叫`_DllMainCRTStartup`可處理 Windows OS 訊息所要附加或中斷連結處理序或執行緒的 dll。 `_DllMainCRTStartup`函式會執行基本工作，例如堆疊緩衝區安全性設定，C 執行階段程式庫 (CRT) 初始化及終止，而且會呼叫建構函式和解構函式靜態和全域物件。 `_DllMainCRTStartup` 也呼叫攔截函式的其他程式庫，例如 WinRT、 MFC 和 ATL 來執行他們自己的初始化及終止。 而不需要這項初始化、 CRT 和其他程式庫，以及靜態變數，就會處於未初始化的狀態。 相同的 VCRuntime 內部初始化和終止常式會呼叫是否以靜態方式連結的 CRT 或動態連結的 CRT DLL，會使用您的 DLL。

## <a name="default-dll-entry-point-dllmaincrtstartup"></a>預設 DLL 進入點 _DllMainCRTStartup

在 Windows 中，所有的 Dll 可以包含選擇性的進入點函式，通常稱為`DllMain`，也就是呼叫初始化及終止。 這會讓您有機會來配置或釋放所需的其他資源。 Windows 在四種情況下呼叫進入點函式： 處理序連結、 處理序中斷連結、 執行緒連結和中斷連結執行緒。 當 DLL 載入處理序位址空間，使用它的應用程式載入時，或應用程式要求在執行階段 DLL 時，作業系統會建立另一份 DLL 資料。 這就叫做*處理序附加*。 *執行緒附加*DLL 載入程序會建立新的執行緒時，就會發生。 *執行緒卸離*時發生的執行緒終止時，並*處理序中斷連結*已不再需要 DLL，並發行應用程式時，就。 作業系統會個別呼叫 DLL 進入點的每個事件，並傳遞*原因*每個事件類型的引數。 例如，OS 會傳送`DLL_PROCESS_ATTACH`作為*原因*訊號處理程序的引數附加。

VCRuntime 程式庫提供進入點函式，呼叫`_DllMainCRTStartup`處理預設初始化及終止作業。 處理序附加，`_DllMainCRTStartup`函式設定緩衝區安全性檢查，初始化 CRT 和其他程式庫、 初始化執行階段類型資訊、 初始化並呼叫建構函式靜態及非區域的資料，初始化執行緒區域儲存區會遞增每個附加，內部靜態計數器，然後呼叫 使用者或程式庫-提供`DllMain`。 處理序中斷連結，函式會執行反向的這些步驟。 它會呼叫`DllMain`遞減內部的計數器，會呼叫解構函式，呼叫 CRT 終止函式，並註冊`atexit`函式，並通知終止的任何其他程式庫。 附件計數器歸零時，此函數會傳回`FALSE`來向 Windows 可以卸載 DLL。 `_DllMainCRTStartup`期間的執行緒也會呼叫函式連結和中斷連結執行緒。 在這些情況下，VCRuntime 程式碼沒有任何額外的初始化或終止，並只會呼叫`DllMain`傳遞的訊息。 如果`DllMain`會傳回`FALSE`從處理序附加時，發出訊號失敗時，`_DllMainCRTStartup`呼叫`DllMain`一次，並傳遞`DLL_PROCESS_DETACH`作為*原因*引數，然後會經歷的其餘部分終止程序。

建置 Visual c + + 中的預設進入點的 Dll 時`_DllMainCRTStartup`所提供的 VCRuntime 就會自動連結中。 您不需要使用的進入點函式指定您的 DLL [/ENTRY （進入點符號）](../build/reference/entry-entry-point-symbol.md)連結器選項。

> [!NOTE]
> 雖然您可以使用來指定另一個進入點函式的 dll /ENTRY： 連結器選項，我們不建議您這麼做，因為您的進入點函式都必須重複的所有項目，`_DllMainCRTStartup`的話，會以相同的順序。 VCRuntime 提供可讓您重複其行為的函式。 例如，您可以呼叫[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)立即處理序附加到支援[/GS （緩衝區安全性檢查）](../build/reference/gs-buffer-security-check.md)核取選項的緩衝區。 您可以呼叫`_CRT_INIT`函式，將相同的參數傳遞做為進入點函式，來執行 DLL 初始化或終止函式的其餘部分。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>初始化 DLL

您的 DLL 可能會有您的 DLL 載入時必須執行的初始化程式碼。 為了讓您執行您自己的 DLL 初始化及終止函式，`_DllMainCRTStartup`呼叫的函式呼叫`DllMain`，您可以提供。 您`DllMain`必須擁有所需的 DLL 進入點簽章。 預設進入點函式`_DllMainCRTStartup`呼叫`DllMain`Windows 所使用的相同參數傳遞。 根據預設，如果您未提供`DllMain`函式，Visual c + + 為您提供並將其連結中以便`_DllMainCRTStartup`一律會有要呼叫的項目。 這表示，如果您不需要初始化您的 DLL，就沒有什麼特別您只需要建置 DLL 時。

這是用於簽章`DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

某些程式庫包裝`DllMain`為您的函式。 例如，在 MFC DLL，可實作`CWinApp`物件的`InitInstance`和`ExitInstance`執行初始化及終止您的 DLL 所需的成員函式。 如需詳細資訊，請參閱 < [regular 初始化 MFC Dll](#initializing-regular-dlls)一節。

> [!WARNING]
> 進行的動作可以安全地在 DLL 進入點有重大的限制。 請參閱[的一般最佳作法](/windows/desktop/Dlls/dynamic-link-library-best-practices)呼叫中不安全的特定 Windows Api 的`DllMain`。 如果您需要的任何內容，不過最簡單的初始設定然後這麼做在初始化函式的 dll。 您可以要求應用程式呼叫之後的初始化函式`DllMain`已執行，並在它們之前呼叫任何其他函式在 DLL 中。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化 Dll 一般 (非 MFC)

若要使用 VCRuntime 提供的一般 (非 MFC) Dll 中執行您自己的初始化`_DllMainCRTStartup`進入點，您的 DLL 程式碼必須包含函式，呼叫`DllMain`。 下列程式碼顯示顯示何種定義的基本架構`DllMain`看起來會像：

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
> 較舊的 Windows SDK 文件指出，必須在連結器 /ENTRY 選項與命令列上指定 DLL 進入點函式的實際名稱。 使用 Visual c + + 中，您不需要使用 /ENTRY 選項，如果您的進入點函式的名稱是`DllMain`。 事實上，如果您使用名稱與 /ENTRY 選項您進入點函式項目以外`DllMain`，CRT 不會無法適當地初始化您的進入點函式進行相同的初始化呼叫，除非`_DllMainCRTStartup`讓。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>初始化 MFC 的標準 Dll

因為 MFC 的標準 Dll`CWinApp`物件時，他們應該在 MFC 應用程式的相同位置中執行初始化及終止工作： 在`InitInstance`並`ExitInstance`成員函式的 dll `CWinApp`-衍生類別。 因為 MFC 會提供`DllMain`由所呼叫的函式`_DllMainCRTStartup`的`DLL_PROCESS_ATTACH`並`DLL_PROCESS_DETACH`，您不應該撰寫您自己`DllMain`函式。 MFC 提供`DllMain`函式會呼叫`InitInstance`當您的 DLL 載入，而且它會呼叫`ExitInstance`卸載 DLL 之前。

MFC DLL 可以追蹤的多個執行緒藉由呼叫[TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)並[TlsGetValue](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)在其`InitInstance`函式。 這些函式可讓 DLL 儲存執行緒特定資料。

在您的標準 MFC DLL 動態連結至 MFC，如果您使用任何 MFC OLE，MFC 資料庫 （或 DAO） 或 MFC 通訊端支援，分別偵錯 MFC 擴充 Dll MFCO*版本*d.d、 MFCD*版本*D.d 和 MFCN*版本*d.d (其中*版本*是版本號碼) 會自動連結中。 您必須呼叫其中一個下列預先定義函式初始化每個您標準的 MFC DLL 中使用這些 Dll `CWinApp::InitInstance`。

|MFC 支援的類型|若要呼叫的初始化函式|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*版本*d.d)|`AfxOleInitModule`|
|MFC 資料庫 (MFCD*版本*d.d)|`AfxDbInitModule`|
|MFC 通訊端 (MFCN*版本*d.d)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 擴充 Dll

因為 MFC 擴充 Dll 並沒有`CWinApp`-衍生物件 （如執行標準 MFC Dll），您應該加入您初始化及終止程式碼`DllMain`MFC DLL 精靈產生的函式。

精靈會將下列程式碼提供 MFC 擴充 Dll。 在程式碼的`PROJNAME`是您的專案名稱的預留位置。

```cpp
#include "stdafx.h"
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

建立新`CDynLinkLibrary`在初始化期間的物件可讓 MFC 擴充 DLL 匯出`CRuntimeClass`物件或用戶端應用程式的資源。

如果您要使用您的 MFC 擴充 DLL 從一或多個標準的 MFC Dll，您必須將匯出的初始化函式會建立`CDynLinkLibrary`物件。 從每個使用 MFC 擴充 DLL 的標準 MFC Dll，就必須呼叫該函式。 呼叫初始化函式的適當位置處於`InitInstance`成員函式的標準 MFC DLL 的`CWinApp`-使用任何 MFC 擴充 DLL 匯出的類別或函式之前衍生物件。

在`DllMain`，MFC DLL 精靈產生時，呼叫`AfxInitExtensionModule`擷取模組的執行階段類別 (`CRuntimeClass`結構) 以及其物件處理站 (`COleObjectFactory`物件) 的使用時機`CDynLinkLibrary`建立物件。 您應該檢查的傳回值`AfxInitExtensionModule`; 如果從傳回值為零`AfxInitExtensionModule`，傳回零，從您`DllMain`函式。

如果您的 MFC 擴充 DLL 將會明確地連結到可執行檔 (這表示可執行檔呼叫`AfxLoadLibrary`若要連結至 DLL)，您應該將呼叫加入`AfxTermExtensionModule`上`DLL_PROCESS_DETACH`。 此函式可讓每個處理序中斷連結 MFC 擴充 DLL 時清除 MFC 擴充 DLL 的 MFC (處理序結束時，或可能是卸載 DLL，恰好`AfxFreeLibrary`呼叫)。 如果您的 MFC 擴充 DLL 將會以隱含方式連結到應用程式中，呼叫`AfxTermExtensionModule`不需要。

明確連結至 MFC 擴充 Dll 必須呼叫的應用程式`AfxTermExtensionModule`時釋放 DLL。 它們也應該使用`AfxLoadLibrary`並`AfxFreeLibrary`(而不是 Win32 函式`LoadLibrary`和`FreeLibrary`) 應用程式使用多個執行緒。 使用`AfxLoadLibrary`和`AfxFreeLibrary`可確保當載入及卸載 DLL 的 MFC 延伸模組不會不會損毀的通用的 MFC 狀態時執行的啟動和關閉程式碼。

因為時間完全初始化 MFCx0.dll`DllMain`是呼叫，您可以配置記憶體並呼叫 MFC 的函式內`DllMain`（不同於 MFC 的 16 位元版本）。

擴充 Dll 可以處理多執行緒處理`DLL_THREAD_ATTACH`並`DLL_THREAD_DETACH`情況下，在`DllMain`函式。 這些情況下會傳遞至`DllMain`時附加執行緒，並從 DLL 卸離。 呼叫[TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc) DLL 連接時，可讓 DLL 維護的執行緒區域儲存區 (TLS) 編製索引，每個執行緒附加到 DLL。

請注意，標頭檔 Afxdllx.h 包含特殊的定義，在 MFC 擴充 Dll，例如的定義中使用的結構`AFX_EXTENSION_MODULE`和`CDynLinkLibrary`。 您應該在您的 MFC 擴充 DLL 中包含此標頭檔。

> [!NOTE]
>  很重要，您不定義或取消定義的任何`_AFX_NO_XXX`Stdafx.h 中的巨集。 這些巨集存在目的只檢查特定的目標平台是否支援該功能，或不。 您可以撰寫程式來檢查這些巨集 (比方說， `#ifndef _AFX_NO_OLE_SUPPORT`)，但您的程式應該永遠不會定義或取消這些巨集。

範例初始化函式中所包含的多執行緒的控制代碼[使用執行緒本機儲存體中的動態連結程式庫](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library)Windows SDK 中。 請注意，此範例包含呼叫的進入點函式`LibMain`，但您應該為此函式命名`DllMain`，讓它運作的 MFC 和 C 執行階段程式庫。

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)<br/>
[DllMain 進入點](/windows/desktop/Dlls/dllmain)<br/>
[動態連結程式庫的最佳作法](/windows/desktop/Dlls/dynamic-link-library-best-practices)
