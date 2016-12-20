---
title: "動態連結至 MFC 的標準 DLL | Microsoft Docs"
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
  - "AFX_MANAGE_STATE 巨集"
  - "DLL [C++], 規則性"
  - "動態連結的 DLL [C++]"
  - "標準 DLL [C++], 動態連結至 MFC"
  - "共用的 DLL 版本 [C++]"
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 動態連結至 MFC 的標準 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

動態連結至 MFC 的標準 DLL 是內部使用 MFC 的 DLL，而 DLL 裡的匯出函式可以由 MFC 或非 MFC 可執行檔呼叫。  如同名稱所說明的，這類型的 DLL 是使用 MFC 的動態連結程式庫版本 \(也稱為 MFC 的共用版本\) 來建置。  函式通常是從使用標準 C 介面的標準 DLL 來匯出。  
  
 您必須將 `AFX_MANAGE_STATE` 巨集加入至標準 DLL 中所有匯出之函式的開頭 \(DLL 會動態連結至 MFC\)，將目前的模組狀態設定為 DLL 的狀態。  這個部分可藉由將下行程式碼加入由 DLL 匯出的函式開頭來完成：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 動態連結至 MFC 的標準 DLL 有下列功能：  
  
-   這種新類型的 DLL 是由 Visual C\+\+ 4.0 引入。  
  
-   用戶端可執行檔可以使用任何支援 DLL 用法的語言來撰寫 \(C、C\+\+、Pascal、Visual Basic 等等\)；它不一定要是 MFC 應用程式。  
  
-   不同於靜態連結的標準 DLL，這類型的 DLL 是動態連結至 MFC DLL \(也稱為共用的 MFC DLL\)。  
  
-   連結至這類 DLL 的 MFC 匯入程式庫，與使用 MFC DLL 的擴充 DLL 或應用程式所使用的相同：MFCxx\(D\).LIB。  
  
 動態連結至 MFC 的標準 DLL 有下列需求：  
  
-   這些 DLL 在已定義 **\_AFXDLL** 的情況下編譯，就像動態連結至 MFC DLL 的可執行檔一樣。  但是也會定義 **\_USRDLL**，就像靜態連結至 MFC 的標準 DLL 一樣。  
  
-   這類型的 DLL 必須產生 `CWinApp` 衍生類別。  
  
-   這類的 DLL 會使用 MFC 所提供的 `DllMain`。  將所有 DLL 特定的初始化程式碼置於 `InitInstance` 成員函式，以及將終止程式碼置於 `ExitInstance` 裡，如同一般 MFC 應用程式裡一樣。  
  
 因為這類 DLL 使用 MFC 的動態連結程式庫版本，所以您必須明確地將目前模組狀態設定為 DLL 的狀態。  若要這樣做，請在每個 DLL 匯出的函式開頭使用 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 巨集。  
  
 標準 DLL 必須像 MFC 應用程式一樣，擁有 `CWinApp` 衍生類別和此應用程式類別的單一物件。  然而，DLL 的 `CWinApp` 物件並不像應用程式的 `CWinApp` 物件，其沒有主要的訊息幫浦。  
  
 請注意因為應用程式擁有主要訊息幫浦，所以 `CWinApp::Run` 機制不適用於 DLL。  如果 DLL 開啟非強制回應的對話方塊或者是有它自己的主框架視窗，應用程式的主要訊息幫浦就必須呼叫將會呼叫 `CWinApp::PreTranslateMessage` 的 DLL 匯出常式。  
  
 像在一般 MFC 應用程式一樣，將所有 DLL 特定的初始化置於 `CWinApp::InitInstance` 成員函式裡。  `CWinApp` 衍生類別的 `CWinApp::ExitInstance` 成員函式，會在 DLL 卸載之前由 MFC 提供的 `DllMain` 函式所呼叫。  
  
 您必須將共用的 DLL，MFCx0.dll 和 Msvcr\*0.dll \(或類似檔案\)，與應用程式一起散佈。  
  
 動態連結至 MFC 的 DLL 也無法靜態地連結至 MFC。  應用程式會像其他任何的 DLL 一樣，連結到已動態連結至 MFC 的標準 DLL。  
  
 符號通常是由使用標準 C 介面的標準 DLL 匯出。  由標準 DLL 匯出的函式宣告看起來像這樣：  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 標準 DLL 內的所有記憶體配置應該在 DLL 維持；DLL 應該不要從呼叫的可執行檔傳遞或接收下列任何一項：  
  
-   MFC 物件的指標。  
  
-   由 MFC 配置之記憶體的指標。  
  
 如果您需要做上述的任何一項，或者您需要在呼叫的可執行檔和 DLL 之間傳遞 MFC 衍生物件，您就必須建置擴充 DLL。  
  
 只有當您將資料做複本時，將指標傳遞到由應用程式和 DLL 之間的 C 執行階段程式庫配置的記憶體才是安全的。  您千萬不可在未製作記憶體複本情況下刪除或調整這些指標的大小，或者使用它們。  
  
 您需要在建置動態連結至 MFC 的標準 DLL 時，使用巨集 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 來正確地切換 MFC 模組狀態。  這個部分可藉由將下行程式碼加入由 DLL 匯出的函式開頭來完成：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 **AFX\_MANAGE\_STATE** 巨集不應該用於會靜態連結至 MFC 的標準 DLL 或擴充 DLL 裡。  如需詳細資訊，請參閱[管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)。  
  
 如需如何撰寫、建置和使用標準 DLL 的範例，請參閱 [DLLScreenCap](http://msdn.microsoft.com/zh-tw/2171291d-3a50-403b-90a1-d93c2acb4f4a) 範例。  如需動態連結至 MFC 的標準 DLL 的詳細資訊，請參閱＜將 DLLScreenCap 轉換為與 MFC DLL 動態連結＞章節中的範例摘要。  
  
## 您想要執行甚麼工作？  
  
-   [初始化標準 DLL](../build/initializing-regular-dlls.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [動態連結至 MFC 之標準 DLL 的模組狀態](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [將 MFC 當成 DLL 的一部分來使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## 請參閱  
 [DLL 的類型](../build/kinds-of-dlls.md)