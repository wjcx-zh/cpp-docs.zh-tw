---
title: "在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 擴充功能"
  - "DLL [C++], 初始化"
  - "DLL [C++], 規則性"
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從標準 DLL 使用擴充 DLL 時，如果擴充 DLL 沒有連結至標準 DLL 的 **CDynLinkLibrary** 物件鏈結，則您可能會遇到一或多組的相關問題。  因為偵錯版的 MFC 資料庫、OLE 和通訊端支援 DLL 會實作為擴充 DLL，所以您可能會在使用這些 MFC 功能時遇到類似的問題，即使您並沒有明確地使用任何自己的擴充 DLL。  有些症狀是：  
  
-   嘗試解除序列化定義在擴充 DLL 裡的類別型別的物件時，訊息「警告：無法從保存載入 CYourClass。  沒有定義類別。」會出現在 TRACE 偵錯視窗，而且無法序列化該物件。  
  
-   此時可能會擲回表示錯誤類別的例外狀況。  
  
-   因為 `AfxFindResourceHandle` 傳回 **NULL** 或不正確的資源控制代碼，因此無法載入儲存於擴充 DLL 的資源。  
  
-   `DllGetClassObject`、`DllCanUnloadNow` 和 `COleObjectFactory` 的 `UpdateRegistry`、`Revoke`、`RevokeAll` 和 `RegisterAll` 成員函式無法找出在擴充 DLL 裡定義的 Class Factory。  
  
-   `AfxDoForAllClasses` 無法用於擴充 DLL 裡的任何類別。  
  
-   無法載入標準 MFC 資料庫、通訊端或 OLE 資源。  例如，**AfxLoadString**\(**AFX\_IDP\_SQL\_CONNECT\_FAIL**\) 會傳回空字串，即使標準 DLL 已適當地使用 MFC 資料庫類別。  
  
 這些問題的解決方法是建立並匯出一個用來建立 **CDynLinkLibrary** 物件的擴充 DLL 之初始化函式。  從每個使用擴充 DLL 的標準 DLL 中，確實地只呼叫一次初始化函式。  
  
## MFC OLE、MFC 資料庫 \(或 DAO\) 或 MFC 通訊端支援  
 如果您在自己的標準 DLL 中使用任何的 MFC OLE、MFC 資料庫 \(或 DAO\) 或 MFC 通訊端支援，則 MFC 偵錯版的擴充 DLL MFCOxxD.dll、MFCDxxD.dll 和 MFCNxxD.dll \(xx 是版本號碼\) 會分別自動地連結。  您必須為您要使用的每一個 DLL 呼叫預先定義的初始化函式。  
  
 為了使用資料庫支援，請在您的標準 DLL 的 `CWinApp::InitInstance` 函式中加入 `AfxDbInitModule` 的呼叫。  請確定在任何基底類別呼叫或存取 MFCDxxD.dll 之新增的程式碼之前執行這個呼叫。  這個函式不會使用參數且會傳回虛值 \(Void\)。  
  
 為了使用 OLE 支援，請在您的標準 DLL 的 `CWinApp::InitInstance` 中加入 `AfxOleInitModule` 呼叫。  請注意，**COleControlModule InitInstance** 函式已經呼叫 `AfxOleInitModule`，因此如果您正在建置 OLE 控制項且將使用 `COleControlModule`，您就不應該加入 `AfxOleInitModule` 呼叫。  
  
 為了使用通訊端支援，請在您的標準 DLL 的 `CWinApp::InitInstance` 中加入 `AfxNetInitModule` 呼叫。  
  
 請注意，MFC DLL 的發行版和應用程式並不會對資料庫、通訊端或 OLE 支援使用不同的 DLL。  然而，在發行模式裡可以安全地呼叫這些初始化函式。  
  
## CDynLinkLibrary 物件  
 在本主題開頭所述的每個作業期間，MFC 會需要搜尋必要的值或物件。  例如，在還原序列化 \(Deserialization\) 期間，MFC 需要搜尋目前所有可用的執行階段類別，比對在封存中的物件和其適當的執行階段類別。  
  
 做為這些搜尋的一部分，MFC 會逐一查看 **CDynLinkLibrary** 物件的鏈結，掃描所有使用中的擴充 DLL。  **CDynLinkLibrary** 物件會在建構期間自動連結至鏈結，並且依序在初始化期間由每個擴充 DLL 建立。  此外，每一個模組 \(應用程式或標準 DLL\) 有它自己的 **CDynLinkLibrary** 物件鏈結。  
  
 為了讓擴充 DLL 連結至 **CDynLinkLibrary** 鏈結，它必須在每個使用擴充 DLL 的模組內容中建立 **CDynLinkLibrary** 物件。  因此，如果擴充 DLL 是要從標準 DLL 裡使用，它必須提供建立 **CDynLinkLibrary** 物件的匯出初始化功能。  每一個使用擴充 DLL 的標準 DLL 必須呼叫匯出的初始化函式。  
  
 如果擴充 DLL 只用於 MFC 應用程式 \(.exe\) 且不用於標準 DLL，則在擴充 DLL 的 `DllMain` 中建立 **CDynLinkLibrary** 物件就已足夠。  這便是 MFC DLL 精靈擴充 DLL 程式碼的功能。  隱含載入擴充 DLL 時，`DllMain` 會在應用程式啟動之前載入並執行。  任何 **CDynLinkLibrary** 建立會連結至 MFC DLL 為 MFC 應用程式保留的預設鏈結裡。  
  
 請注意，在任何一個鏈結中放置多個來自同一個擴充 DLL 的 **CDynLinkLibrary** 物件並不是個好方法，特別是如果擴充 DLL 會從記憶體動態地卸載之時。  不要從任何一個模組超過一次地呼叫初始化函式。  
  
## 程式碼範例  
 這個範例程式碼假設標準 DLL 會隱含連結至擴充 DLL。  這項操作藉由在建置標準 DLL 時連結至擴充 DLL 的匯入程式庫 \(.lib\) 來完成。  
  
 以下幾行程式碼應該會出現在擴充 DLL 的原始程式碼中：  
  
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
        // extension DLL one-time initialization  
        if (!AfxInitExtensionModule(extensionDLL, hInstance))  
           return 0;  
    }  
    return 1;   // ok  
}  
  
// Exported DLL initialization is run in context of  
// application or regular DLL  
extern "C" void WINAPI InitYourExtDLL()  
{  
    // create a new CDynLinkLibrary for this app  
    new CDynLinkLibrary(extensionDLL);  
  
    // add other initialization here  
}  
```  
  
 確定要匯出 **InitYourExtDLL** 函式。  這項操作可以使用 **\_\_declspec\(dllexport\)** 或依照下列方式在 DLL 的 .def 檔中完成：  
  
```  
// YourExtDLL.Def:  
LIBRARY      YOUREXTDLL  
CODE         PRELOAD MOVEABLE DISCARDABLE  
DATA         PRELOAD SINGLE  
EXPORTS  
    InitYourExtDLL  
```  
  
 在每個使用擴充 DLL 的標準 DLL 中加入 `CWinApp` 衍生物件 `InitInstance` 成員的呼叫：  
  
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
    TRACE0("YOUR regular DLL initializing\n");  
  
    // wire any extension DLLs into CDynLinkLibrary chain  
    InitYourExtDLL();  
  
    return TRUE;  
}  
```  
  
### 您想要執行甚麼工作？  
  
-   [初始化擴充 DLL](../build/initializing-extension-dlls.md)  
  
-   [初始化標準 DLL](../build/initializing-regular-dlls.md)  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [擴充 DLL](../build/extension-dlls.md)  
  
-   [靜態連結至 MFC 的標準 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [將 MFC 當成 DLL 的一部分來使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
## 請參閱  
 [擴充 DLL](../build/extension-dlls.md)