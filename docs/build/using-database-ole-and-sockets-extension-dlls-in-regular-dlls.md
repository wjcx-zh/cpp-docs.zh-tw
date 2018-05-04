---
title: 在 MFC 的標準 Dll 中使用資料庫、 OLE 和通訊端 MFC 擴充 Dll |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f902f3b512b5684cf185829fdf4346b8851ff8ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>在 MFC 的標準 Dll 中使用資料庫、 OLE 和通訊端 MFC 擴充 Dll
當您使用 MFC 擴充 DLL 從標準的 MFC DLL，如果 MFC 擴充 DLL 不有線網路到**CDynLinkLibrary**物件鏈結的標準 MFC DLL，您可能會遇到一或多個一組相關的問題。 因為 MFC 資料庫、 OLE 和通訊端的偵錯版本支援的 Dll 會實作為 MFC 擴充 Dll，您可能會看到類似的問題，如果您使用這些 MFC 功能，即使您未明確使用任何您自己的 MFC 擴充 Dll。 某些徵兆如下：  
  
-   當嘗試還原序列化的類別類型的物件定義在 MFC 擴充 DLL，訊息 「 警告： 無法載入 CYourClass 從封存。 類別未定義。 」 出現在追蹤偵錯視窗與物件無法序列化。  
  
-   可能會擲回例外狀況，指出錯誤的類別。  
  
-   資源儲存在 MFC 擴充 DLL 中無法載入，因為`AfxFindResourceHandle`傳回**NULL**或不正確的資源控制代碼。  
  
-   `DllGetClassObject``DllCanUnloadNow`，而`UpdateRegistry`， `Revoke`， `RevokeAll`，和`RegisterAll`的成員函式`COleObjectFactory`找不到 MFC 擴充 DLL 中定義的類別處理站。  
  
-   `AfxDoForAllClasses` 不適用於任何 MFC 擴充 DLL 中的類別。  
  
-   標準 MFC 資料庫、 通訊端或 / / OLE 資源無法載入。 例如， **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) 會傳回空字串，即使是標準的 MFC DLL 正確使用 MFC 資料庫類別。  
  
 這些問題的解決方案為建立和匯出 MFC 擴充功能建立的 DLL 中的初始化函式**CDynLinkLibrary**物件。 完全之後從每個標準的 MFC DLL 使用 MFC 擴充 DLL，請呼叫初始化函式。  
  
## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE、 MFC 資料庫 （或 DAO），或 MFC 通訊端支援  
 如果您使用任何 MFC OLE、 MFC 資料庫 （或 DAO） 或 MFC 通訊端分別支援標準的 MFC DLL 中，MFC 偵錯 MFC 擴充 Dll MFCOxxD.dll、 MFCDxxD.dll 和 MFCNxxD.dll （其中 xx 是版本號碼） 會自動連結。 您必須針對每個您要使用這些 Dll 呼叫預先定義的初始化函式。  
  
 如需資料庫支援，將呼叫加入`AfxDbInitModule`至您規則的 MFC DLL`CWinApp::InitInstance`函式。 請確定這個呼叫發生之前的任何基底類別呼叫或任何加入的程式碼會存取 MFCDxxD.dll。 此函數會採用任何參數，並傳回 void。  
  
 如需 OLE 支援，將呼叫加入`AfxOleInitModule`至您規則的 MFC DLL `CWinApp::InitInstance`。 請注意， **COleControlModule InitInstance**函式呼叫`AfxOleInitModule`，因此，如果您要建立 OLE 控制項，並使用`COleControlModule`，則不應新增此呼叫`AfxOleInitModule`。  
  
 如需通訊端支援，將呼叫加入`AfxNetInitModule`至您規則的 MFC DLL `CWinApp::InitInstance`。  
  
 請注意，發行組建的 MFC Dll 和應用程式不需要在資料庫中的通訊端，使用個別的 Dll 或 OLE 支援。 不過，它是安全地呼叫這些初始化函式在發行模式中。  
  
## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary 物件  
 在每個作業在本主題開頭所述，MFC 會需要搜尋所要的值或物件。 例如，還原序列化時，MFC 需要搜尋所有目前執行階段類別以符合其適當的執行階段類別與封存中的物件。  
  
 這些搜尋的一部份，MFC 透過掃描使用中的所有 MFC 擴充 Dll 所鏈結的**CDynLinkLibrary**物件。 **CDynLinkLibrary**物件在其建構期間自動附加至鏈結，並接著在初始化期間建立的每個 MFC 擴充 DLL。 此外，每個模組 （應用程式或 MFC 的標準 DLL） 具有自己的鏈結**CDynLinkLibrary**物件。  
  
 MFC 擴充 DLL 至**CDynLinkLibrary**鏈結，就必須建立**CDynLinkLibrary**的每個使用 MFC 擴充 DLL 的模組內容中的物件。 因此，如果 MFC 擴充 DLL 將會從 MFC 的標準 Dll，它必須提供匯出的初始化函式會建立**CDynLinkLibrary**物件。 每個 MFC 使用的標準 DLL MFC 擴充 DLL 必須呼叫匯出的初始化函式。  
  
 如果 MFC 擴充 DLL 只會用於從 MFC 應用程式 (.exe)，並永遠不會從標準的 MFC DLL，則它就足以建立**CDynLinkLibrary**物件在 MFC 擴充 DLL 的`DllMain`。 這是 MFC DLL 精靈 MFC 擴充 DLL 程式碼所執行的工作。 以隱含方式載入的 MFC 擴充 DLL 時`DllMain`載入並執行之前曾啟動應用程式。 任何**CDynLinkLibrary**建立用於有線預設鏈結至 MFC DLL 保留 MFC 應用程式。  
  
 請注意，它是個好主意，有多個**CDynLinkLibrary**物件從一個 MFC 擴充 DLL 中任何一個的鏈結，尤其是 MFC 擴充 DLL 將會以動態方式從記憶體中卸載。 請勿呼叫初始化函式一次從任何一個模組。  
  
## <a name="sample-code"></a>程式碼範例  
 此範例程式碼會假設一般 MFC DLL 會隱含連結至 MFC 擴充 DLL。 這是連結至 MFC 擴充 DLL 匯入程式庫 (.lib)，建置標準的 MFC DLL 時達成。  
  
 MFC 擴充 DLL 的來源應為下列行：  
  
```  
// YourExtDLL.cpp:  
  
// standard MFC extension DLL routines  
#include "afxdllx.h"  
  
static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };  
  
extern "C" int APIENTRY  
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)  
{  
    if (dwReason == DLL_PROCESS_ATTACH)  
    {  
        // MFC extension DLL one-time initialization  
        if (!AfxInitExtensionModule(extensionDLL, hInstance))  
           return 0;  
    }  
    return 1;   // ok  
}  
  
// Exported DLL initialization is run in context of  
// application or regular MFC DLL  
extern "C" void WINAPI InitYourExtDLL()  
{  
    // create a new CDynLinkLibrary for this app  
    new CDynLinkLibrary(extensionDLL);  
  
    // add other initialization here  
}  
```  
  
 請務必匯出**InitYourExtDLL**函式。 可使用 **__declspec （dllexport)** 或 DLL 的.def 檔案，如下所示：  
  
```  
// YourExtDLL.Def:  
LIBRARY      YOUREXTDLL  
CODE         PRELOAD MOVEABLE DISCARDABLE  
DATA         PRELOAD SINGLE  
EXPORTS  
    InitYourExtDLL  
```  
  
 將呼叫加入`InitInstance`隸屬`CWinApp`-衍生物件中每個使用 MFC 擴充 DLL 的標準 MFC DLL:  
  
```  
// YourRegularDLL.cpp:  
  
class CYourRegularDLL : public CWinApp  
{  
public:  
    virtual BOOL InitInstance(); // Initialization  
    virtual int ExitInstance();  // Termination  
  
    // nothing special for the constructor  
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }  
};  
  
BOOL CYourRegularDLL::InitInstance()  
{  
    // any DLL initialization goes here  
    TRACE0("YOUR regular MFC DLL initializing\n");  
  
    // wire any MFC extension DLLs into CDynLinkLibrary chain  
    InitYourExtDLL();  
  
    return TRUE;  
}  
```  
  
### <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [初始化 MFC 擴充 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
-   [初始化 MFC 的標準 Dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [MFC 延伸模組 DLL](../build/extension-dlls.md)  
  
-   [靜態連結至 MFC 的標準 MFC DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 MFC DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [將 MFC 當成 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 延伸模組 DLL](../build/extension-dlls.md)