---
title: Dll 和 Visual c + + 執行階段程式庫行為 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: feee3d888fbf43bfd8675ccc83a04fd4e1f0b528
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392058"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Dll 和 Visual c + + 執行階段程式庫行為  
  
當您建置動態連結程式庫 (DLL) 使用 Visual c + + 中，依預設時，連結器就會包含 Visual c + + 執行階段程式庫 (VCRuntime)。 VCRuntime 包含初始化及終止 C/c + + 可執行檔所需的程式碼。 當連結到 DLL，VCRuntime 程式碼會提供內部 DLL 進入點函式呼叫`_DllMainCRTStartup`可處理 Windows OS 訊息所要附加或中斷處理序或執行緒的 dll。 `_DllMainCRTStartup`函式會執行基本工作，例如堆疊緩衝區安全性設定，C 執行階段程式庫 (CRT) 初始化及終止，而且會呼叫建構函式和解構函式靜態和全域物件。 `_DllMainCRTStartup` 也呼叫攔截函式來執行他們自己的初始化及終止的 WinRT、 MFC 和 ATL 之類的其他程式庫。 沒有這類初始化、 CRT 和其他文件庫，以及您的靜態變數，就會處於未初始化的狀態。 相同 VCRuntime 內部初始化及終止常式會呼叫您的 DLL 會使用靜態連結的 CRT 或動態連結的 CRT DLL。  
  
## <a name="default-dll-entry-point-dllmaincrtstartup"></a>預設 DLL 進入點 _DllMainCRTStartup  
  
在 Windows 中，所有的 Dll 可包含選擇性的進入點函式，通常稱為`DllMain`，也就是呼叫初始化及終止。 這會讓您有機會來配置或釋放所需的其他資源。 Windows 會呼叫進入點函式中四種情況： 處理序附加、 處理序中斷連結、 執行緒附加和卸離執行緒。 當 DLL 載入處理序位址空間中，使用它的應用程式載入時，或當應用程式要求在執行階段 DLL 時，作業系統會建立個別的 DLL 資料複本。 這稱為*處理序附加*。 *執行緒附加*發生於載入 DLL 中的程序建立新的執行緒。 *卸離執行緒*執行緒終止時，就會發生和*處理序中斷連結*時 DLL 已不再需要和發行應用程式。 作業系統會針對每個事件，傳遞個別的 DLL 進入點呼叫*原因*每一個事件型別引數。 例如，作業系統會傳送`DLL_PROCESS_ATTACH`為*原因*附加訊號處理程序的引數。  
  
VCRuntime 程式庫提供進入點函式，呼叫`_DllMainCRTStartup`處理預設初始化及終止作業。 處理序附加，`_DllMainCRTStartup`函式設定緩衝區安全性檢查、 初始化 CRT 和其他文件庫、 初始化執行階段類型資訊、 初始化和呼叫建構函式靜態和非本機資料、 初始化執行緒區域儲存區會遞增每個附加、 內部靜態計數器，然後呼叫 使用者或程式庫-提供`DllMain`。 處理序中斷連結，此函式會進行下列步驟以反向方向。 它會呼叫`DllMain`，遞減內部的計數器，呼叫解構函式，呼叫 CRT 終止函式，並註冊`atexit`函式，並通知終止的任何其他程式庫。 當附件計數器為零，則函數會傳回`FALSE`表示 Windows DLL 可以被卸載。 `_DllMainCRTStartup`期間的執行緒也會呼叫函式附加和卸離執行緒。 在這些情況下，VCRuntime 程式碼沒有任何額外的初始化或終止其本身，並只會呼叫`DllMain`傳遞的訊息。 如果`DllMain`傳回`FALSE`從處理序附加時，正在失敗，發出訊號`_DllMainCRTStartup`呼叫`DllMain`一次，並傳遞`DLL_PROCESS_DETACH`為*原因*引數，然後會通過其餘的終止處理程序。  
  
當建置 Visual c + + 中的預設進入點 Dll`_DllMainCRTStartup`所提供的自動 VCRuntime 連結中。 您不需要指定您的 DLL 進入點函式，使用[/ENTRY （進入點符號）](../build/reference/entry-entry-point-symbol.md)連結器選項。  
  
> [!NOTE]
> 雖然您可以使用來指定另一個進入點函式的 DLL /ENTRY： 連結器選項，我們不建議您這麼做，因為您的進入點函式會有重複的所有項目，`_DllMainCRTStartup`會以相同的順序。 VCRuntime 提供函數，可讓您重複其行為。 例如，您可以呼叫[__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md)立即處理序附加至支援[/GS （緩衝區安全性檢查）](../build/reference/gs-buffer-security-check.md)緩衝區檢查選項。 您可以呼叫`_CRT_INIT`函式，做為進入點函式，來執行 DLL 初始化或終止函式的其餘部分傳遞相同的參數。  
  
<a name="initializing-a-dll"></a>  
  
## <a name="initialize-a-dll"></a>初始化 DLL  
  
您的 DLL，可能必須在載入 DLL 時執行的初始化程式碼。 為了讓您執行您自己的 DLL 初始化及終止函式，`_DllMainCRTStartup`呼叫函式，呼叫`DllMain`可以提供。 您`DllMain`必須具有所需的 DLL 進入點簽章。 預設進入點函式`_DllMainCRTStartup`呼叫`DllMain`Windows 所使用的相同參數傳遞。 根據預設，如果您未提供`DllMain`函式，Visual c + + 為您提供並將它連結中，讓`_DllMainCRTStartup`一定會有要呼叫的項目。 這表示您不需要初始化您的 DLL，如果沒有任何特殊您必須先建置 DLL 時執行。  
  
這是用於簽章`DllMain`:  
  
```cpp  
#include <windows.h>  
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```  
  
有些程式庫包裝`DllMain`為您的函式。 例如，在一般 MFC DLL 中，實作`CWinApp`物件的`InitInstance`和`ExitInstance`執行初始化和終止您的 DLL 所需的成員函式。 如需詳細資訊，請參閱[regular 初始化 MFC Dll](#initializing-regular-dlls) > 一節。  
  
> [!WARNING]
> 您可以安全地中進行的動作 DLL 進入點有重要的限制。 請參閱[的一般最佳作法](https://msdn.microsoft.com/library/windows/desktop/dn633971#general_best_practices)特定的 Windows Api 呼叫中不安全的`DllMain`。 如果您需要有任何作用，然後最簡單的初始設定，在中執行的初始化函式為 DLL。 您可以要求應用程式呼叫之後的初始化函式`DllMain`具有執行和之前呼叫任何其他函式在 DLL 中。  
  
<a name="initializing-non-mfc-dlls"></a>  
  
### <a name="initialize-ordinary-non-mfc-dlls"></a>初始化 Dll 一般 (非 MFC)  
  
若要使用 VCRuntime 提供的一般 (非 MFC) Dll 中執行您自己的初始化`_DllMainCRTStartup`進入點，您的 DLL 程式碼必須包含函式，呼叫`DllMain`。 下列程式碼會顯示哪些定義的基本`DllMain`看起來會像：  
  
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
> 舊版 Windows SDK 文件會指出連結器 /ENTRY 選項與命令列上，必須指定 DLL 進入點函式的實際名稱。 Visual c + + 中，您不需要使用 /ENTRY 選項，如果您的進入點函式的名稱是`DllMain`。 事實上，如果您使用名稱與 /ENTRY 選項進入點以外的函式項目`DllMain`，CRT 不會無法適當地初始化您的進入點函式會初始化呼叫相同，除非`_DllMainCRTStartup`讓。  
  
<a name="initializing-regular-dlls"></a>  
  
### <a name="initialize-regular-mfc-dlls"></a>初始化 MFC 的標準 Dll  
  
因為標準的 MFC Dll 具有`CWinApp`物件、 初始化及終止工作應該執行 MFC 應用程式的相同位置中： 在`InitInstance`和`ExitInstance`成員函式的 dll `CWinApp`-衍生類別。 由於 MFC 提供`DllMain`函式所呼叫`_DllMainCRTStartup`如`DLL_PROCESS_ATTACH`和`DLL_PROCESS_DETACH`，不應該寫入您自己的`DllMain`函式。 MFC 提供`DllMain`函式呼叫`InitInstance`當已載入您的 DLL，而且它會呼叫`ExitInstance`DLL 卸載之前。  
  
標準的 MFC DLL 可以追蹤的多個執行緒藉由呼叫[TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801)和[TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812)中其`InitInstance`函式。 這些函數可讓 DLL 儲存執行緒特定資料。  
  
在一般 MFC DLL 動態連結至 MFC 中，如果您使用任何 MFC OLE、 MFC 資料庫 （或 DAO），或分別 MFC 通訊端支援偵錯 MFC 擴充 Dll MFCO*版本*d.d、 MFCD*版本*D.d 和 MFCN*版本*d.d (其中*版本*是版本號碼) 會自動連結中。 您必須針對每個您在一般的 MFC DLL 中使用這些 Dll 呼叫下列預先定義的初始化函式的其中一個`CWinApp::InitInstance`。  
  
|MFC 支援的型別|若要呼叫的初始化函式|  
|-------------------------|-------------------------------------|  
|MFC OLE (MFCO*版本*d.d)|`AfxOleInitModule`|  
|MFC 資料庫 (MFCD*版本*d.d)|`AfxDbInitModule`|  
|MFC 通訊端 (MFCN*版本*d.d)|`AfxNetInitModule`|  
  
<a name="initializing-extension-dlls"></a>  
  
### <a name="initialize-mfc-extension-dlls"></a>初始化 MFC 擴充 Dll  
  
因為 MFC 擴充 Dll 並沒有`CWinApp`-衍生物件 （如執行標準的 MFC Dll），您應該加入初始化及終止程式碼以`DllMain`MFC DLL 精靈產生的函式。  
  
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
  
建立新`CDynLinkLibrary`初始化期間的物件可讓 MFC 擴充 DLL 匯出`CRuntimeClass`物件或用戶端應用程式的資源。  
  
如果您要使用您的 MFC 擴充 DLL 從一或多個標準的 MFC Dll，您必須匯出初始化函式會建立`CDynLinkLibrary`物件。 從每個使用 MFC 擴充 DLL 的標準 MFC dll，就必須呼叫該函式。 呼叫初始化函式的適當位置是在`InitInstance`成員函式的標準 MFC DLL 的`CWinApp`-衍生物件使用任何 MFC 擴充 DLL 匯出的類別或函式之前。  
  
在`DllMain`，MFC DLL 精靈產生時，呼叫`AfxInitExtensionModule`擷取模組的執行階段類別 (`CRuntimeClass`結構) 以及其物件處理站 (`COleObjectFactory`物件) 的使用時機`CDynLinkLibrary`建立物件。 您應該檢查傳回值`AfxInitExtensionModule`; 如果為零的值會傳回從`AfxInitExtensionModule`，傳回從零您`DllMain`函式。  
  
如果您的 MFC 擴充 DLL 連結將明確的可執行檔 (這表示可執行檔呼叫`AfxLoadLibrary`連結至 DLL)，您應該將呼叫加入`AfxTermExtensionModule`上`DLL_PROCESS_DETACH`。 此函式可讓 MFC 清除 MFC 擴充 DLL，每個處理序中斷連結從 MFC 擴充 DLL 時 (也就是處理序結束時，或可能是卸載 DLL，`AfxFreeLibrary`呼叫)。 如果您的 MFC 擴充 DLL 將會隱含地連結到應用程式中，呼叫`AfxTermExtensionModule`不需要。  
  
應用程式，必須先明確地呼叫 MFC 擴充 Dll 連結`AfxTermExtensionModule`時釋放 DLL。 它們也應該使用`AfxLoadLibrary`和`AfxFreeLibrary`(而不是 Win32 函式`LoadLibrary`和`FreeLibrary`) 應用程式使用多個執行緒。 使用`AfxLoadLibrary`和`AfxFreeLibrary`可確保 MFC 擴充 DLL 會載入並卸載未損毀全域 MFC 狀態時執行的啟動和關閉程式碼。  
  
因為 MFCx0.dll 完全初始化的時間`DllMain`是呼叫，您可以配置記憶體並呼叫 MFC 的函式內`DllMain`（不同於 MFC 的 16 位元版本）。  
  
擴充 Dll 將會處理多執行緒處理`DLL_THREAD_ATTACH`和`DLL_THREAD_DETACH`案例中`DllMain`函式。 這些情況下會傳遞至`DllMain`執行緒的附加時，並從 DLL 卸離。 呼叫[TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) DLL 附加時，可讓 DLL 維護的執行緒區域儲存區 (TLS) 索引的每個執行緒附加至 DLL。  
  
請注意，標頭檔 Afxdllx.h 包含特殊 MFC 擴充 Dll，例如的定義中使用的結構定義`AFX_EXTENSION_MODULE`和`CDynLinkLibrary`。 您應該在您的 MFC 擴充 DLL 中包含此標頭檔。  
  
> [!NOTE]
>  請務必確認您定義都未定義任何`_AFX_NO_XXX`Stdafx.h 中的巨集。 這些巨集存在只為了檢查是否是特定的目標平台是否支援該功能。 您可以撰寫您的程式來檢查這些巨集 (例如， `#ifndef _AFX_NO_OLE_SUPPORT`)，但您的程式應該永遠不會定義或取消這些巨集。  
  
多執行緒處理的控制代碼隨附於範例初始化函式[使用執行緒區域儲存區中之動態連結程式庫](http://msdn.microsoft.com/library/windows/desktop/ms686997)Windows SDK 中。 請注意，此範例包含呼叫的進入點函式`LibMain`，但您應該將此函式`DllMain`使其可與 MFC 與 C 執行階段程式庫。  
  
## <a name="see-also"></a>另請參閱  
  
[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)  
[DllMain 進入點](https://msdn.microsoft.com/library/windows/desktop/ms682583.aspx)  
[動態連結程式庫的最佳作法](https://msdn.microsoft.com/library/windows/desktop/dn633971.aspx)  