---
title: "初始化擴充 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "擴充 DLL [C++], 初始化"
  - "初始化 DLL"
ms.assetid: 08ad0381-3808-4bea-a93c-c9ba62496543
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 初始化擴充 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

因為擴充 DLL 沒有 `CWinApp` 衍生物件 \(如同標準 DLL\)，所以您應該將初始化和終止程式碼加入到 MFC DLL 精靈產生的 `DllMain` 函式。  
  
 這個精靈會提供擴充 DLL 下列程式碼。  在下列程式碼中，`PROJNAME` 是您專案名稱的替代符號 \(Placeholder\)。  
  
```  
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
  
      // Extension DLL one-time initialization  
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
  
 在初始化期間建立新 **CDynLinkLibrary** 物件可以讓擴充 DLL 將 `CRuntimeClass` 物件或資源匯出到用戶端應用程式。  
  
 如果您要從一或多個標準 DLL 使用您的擴充 DLL，您必須匯出一個會建立 **CDynLinkLibrary** 物件的初始化函式。  該函式必須由每個會使用擴充 DLL 的標準 DLL 來呼叫。  呼叫這個初始化函式的適當地方，是在使用任何擴充 DLL 的匯出類別或函式之前的標準 DLL 的 `CWinApp` 衍生物件 `InitInstance` 成員函式中。  
  
 在 MFC DLL 精靈產生的 `DllMain` 中，`AfxInitExtensionModule` 的呼叫會捕捉模組的 Run\-Time 類別 \(`CRuntimeClass` 物件\)，以及其在建立 **CDynLinkLibrary** 物件所使用的 Object Factory \(`COleObjectFactory` 物件\)。  您應該檢查 `AfxInitExtensionModule` 的傳回值；如果 `AfxInitExtensionModule` 傳回零值，您的 `DllMain` 函式就會傳回零。  
  
 如果您的擴充 DLL 將會明確連接到可執行檔 \(是指可執行檔呼叫 `AfxLoadLibrary` 以連結至 DLL\)，您應該在 **DLL\_PROCESS\_DETACH** 上加入對 `AfxTermExtensionModule` 的呼叫。  這個函式可以讓 MFC 在每個處理序從擴充 DLL 中斷連結時 \(發生在處理序離開或卸載 DLL 來當做 `AfxFreeLibrary` 呼叫的結果時\) 清除擴充 DLL。  如果您的擴充 DLL 會隱含連結至應用程式，`AfxTermExtensionModule` 呼叫就不是必要步驟。  
  
 明確連結至擴充 DLL 的應用程式必須在釋放 DLL 時呼叫 **AfxTermExtensionModule**。  如果應用程式使用多個執行緒，它們也應該使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` \(而不是 Win32 函式 **LoadLibrary** 和 **FreeLibrary**\)。  使用 `AfxLoadLibrary` 和 `AfxFreeLibrary`，可確保載入或卸載擴充 DLL 時所執行的開機與關機程式碼不會毀損全域 MFC 狀態。  
  
 由於 MFCx0.dll 在呼叫 `DllMain` 時會完整地初始化，您可以配置記憶體並且在 `DllMain` \(不同於 MFC 16 位元版\) 內呼叫 MFC 函式。  
  
 擴充 DLL 可以在 `DllMain` 函式裡處理 **DLL\_THREAD\_ATTACH** 和 **DLL\_THREAD\_DETACH** 以便處理多執行緒。  這些情況會在執行緒和 DLL 連結或中斷連結時傳遞至 `DllMain`。  在 DLL 連結時呼叫 [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801)，讓 DLL 為每一個連結至 DLL 的執行緒維持執行緒區域儲存區 \(TLS\) 索引。  
  
 請注意，標頭檔 Afxdllx.h 包含用於擴充 DLL 中的特殊結構定義，例如，`AFX_EXTENSION_MODULE` 和 **CDynLinkLibrary** 的定義。  您應該在您的擴充 DLL 裡包含這個標頭檔。  
  
> [!NOTE]
>  絕對不要在 stdafx.h 中定義或取消定義任何的 \_AFX\_NO\_XXX 巨集。  如需詳細資訊，請參閱知識庫文件＜PRB：定義 \_AFX\_NO\_XXX 時發生問題＞\(Q140751\)。  您可以在 MSDN Library 或是在 [http:\/\/search.support.microsoft.com\/](http://search.support.microsoft.com/) 找到知識庫文件。  
  
 處理多執行緒的初始化函式範例，是包含在 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 的[在動態連結程式庫裡使用執行緒區域儲存區](http://msdn.microsoft.com/library/windows/desktop/ms686997)中。  請注意，此範例包含名為 **LibMain** 的進入點函式，但是您應該以 `DllMain` 命名這個函式，這樣它可以和 MFC 與 C 執行階段程式庫一起使用。  
  
 MFC [DLLHUSK](http://msdn.microsoft.com/zh-tw/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 範例將示範初始化函式的用法。  
  
## 您想要執行甚麼工作？  
  
-   [初始化標準 DLL](../build/initializing-regular-dlls.md)  
  
-   [初始化非 MFC DLL](../build/initializing-non-mfc-dlls.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [C 執行階段程式庫行為和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [\<caps:sentence id\="tgt34" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>DllMain 的函式規格 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt35" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>動態連結程式庫的進入點函式 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
## 請參閱  
 [初始化 DLL](../build/initializing-a-dll.md)