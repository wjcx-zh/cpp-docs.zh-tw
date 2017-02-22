---
title: "靜態連結至 MFC 的標準 DLL | Microsoft Docs"
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
  - "DLL [C++], 規則性"
  - "標準 DLL [C++]"
  - "標準 DLL [C++], 靜態連結至 MFC"
  - "靜態連結的 DLL [C++]"
  - "USRDLL"
  - "USRDLL, 靜態連結至 MFC"
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 靜態連結至 MFC 的標準 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

靜態連結至 MFC 的標準 DLL 是內部使用 MFC 的 DLL，而且 DLL 裡的匯出函式可由 MFC 或非 MFC 可執行檔呼叫。  如同名稱所說明，這類型的 DLL 是使用 MFC 的靜態連結程式庫版本來建置的。  函式通常是從使用標準 C 介面的標準 DLL 來匯出。  如需如何撰寫、建置和使用標準 DLL 的範例，請參閱 [DLLScreenCap](http://msdn.microsoft.com/zh-tw/2171291d-3a50-403b-90a1-d93c2acb4f4a) 範例。  
  
 請注意，Visual C\+\+ 文件裡不再使用 USRDLL 詞彙。  靜態連結至 MFC 的標準 DLL 與之前的 USRDLL 有相同的特性。  
  
 靜態連結至 MFC 的標準 DLL 有下列功能：  
  
-   用戶端可執行檔可以使用任何支援 DLL 用法的語言來撰寫 \(C、C\+\+、Pascal、Visual Basic 等等\)；它不一定要是 MFC 應用程式。  
  
-   DLL 可以連結至應用程式所用的相同 MFC 靜態連結程式庫。  DLL 不再擁有不同版本的靜態連結程式庫。  
  
-   MFC 4.0 版之前，USRDLL 提供與靜態連結至 MFC 之標準 DLL 相同類型的功能。  在 Visual C\+\+ 4.0 版已不再使用 USRDLL 這個詞彙。  
  
 靜態連結至 MFC 的標準 DLL 有下列需求：  
  
-   這類型的 DLL 必須實體化自 `CWinApp` 衍生的類別。  
  
-   這類的 DLL 會使用 MFC 所提供的 `DllMain`。  將所有 DLL 特定的初始化程式碼置於 `InitInstance` 成員函式，以及將終止程式碼置於 `ExitInstance` 裡，如同一般 MFC 應用程式裡一樣。  
  
-   即使已不再使用 USRDLL 這個詞彙，您仍然必須在編譯器 \(Compiler\) 命令列上定義 "**\_USRDLL**"。  這種定義可決定要將何種宣告從 MFC 標頭檔 \(Header File\) 裡納入。  
  
 標準 DLL 必須像 MFC 應用程式一樣，擁有 `CWinApp` 衍生類別和此應用程式類別的單一物件。  然而，DLL 的 `CWinApp` 物件並不像應用程式的 `CWinApp` 物件，其沒有主要的訊息幫浦。  
  
 請注意因為應用程式擁有主要訊息幫浦，所以 `CWinApp::Run` 機制不適用於 DLL。  如果 DLL 開啟了非強制回應 \(Modeless\) 的對話方塊或者有它自己的主框架視窗 \(Main Frame Window\)，應用程式的主要訊息幫浦就必須呼叫由 DLL 匯出的常式，這個常式接著會呼叫 DLL 應用程式物件 \(Application Object\) 的 `CWinApp::PreTranslateMessage` 成員函式。  
  
 如需這個函式的範例，請參閱 DLLScreenCap 範例。  
  
 符號通常是由使用標準 C 介面的標準 DLL 匯出。  由標準 DLL 匯出的函式宣告看起來像這樣：  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 標準 DLL 內的所有記憶體配置應該在 DLL 維持；DLL 應該不要從呼叫的可執行檔傳遞或接收下列任何一項：  
  
-   MFC 物件的指標。  
  
-   由 MFC 配置之記憶體的指標。  
  
 如果您需要做上述的任何一項，或者需要在呼叫的可執行檔和 DLL 之間傳遞 MFC 衍生物件，您就必須建置擴充 DLL。  
  
 只有當您將資料做複本時，將指標傳遞到由應用程式和 DLL 之間的 C 執行階段程式庫配置的記憶體才是安全的。  您千萬不可在未製作記憶體複本情況下刪除或調整這些指標的大小，或者使用它們。  
  
 靜態連結至 MFC 的 DLL 也不能動態連結至共用的 MFC DLL。  靜態連結至 MFC 的 DLL 會像其他任何 DLL 動態地繫結至應用程式；應用程式會像其他任何 DLL 地連結到該 DLL。  
  
 標準 MFC 靜態連結程式庫是根據 [MFC DLL 命名慣例](../build/naming-conventions-for-mfc-dlls.md)所述的慣例來命名。  然而，使用 MFC 3.0 版和之後的版本，您就不再需要手動地為連結器指定您要連結的 MFC 程式庫版本。  相反的，MFC 標頭檔會根據前置處理器定義，自動地決定要連結的正確 MFC 程式庫版本，例如 **\_DEBUG** or **\_UNICODE**。  MFC 標頭檔會加入 \/DEFAULTLIB 指示詞，指示連結器連結特定的 MFC 程式庫版本。  
  
## 您想要執行甚麼工作？  
  
-   [初始化標準 DLL](../build/initializing-regular-dlls.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [將 MFC 當成 DLL 的一部分來使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [建立 MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [擴充 DLL](../build/extension-dlls-overview.md)  
  
## 請參閱  
 [DLL 的類型](../build/kinds-of-dlls.md)