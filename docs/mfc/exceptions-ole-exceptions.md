---
title: "例外狀況：OLE 例外狀況 | Microsoft Docs"
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
  - "例外狀況處理, OLE"
  - "例外狀況, OLE"
  - "OLE 例外狀況"
  - "OLE 例外狀況, 處理的類別"
  - "OLE, 例外狀況"
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 例外狀況：OLE 例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

技術和工具處理的例外狀況在 OLE 與處理的其他例外狀況。  如需例外狀況處理的詳細資訊，請參閱本文件的 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)。  
  
 所有例外狀況物件從抽象基底類別衍生自 `CException`。  MFC 提供處理 OLE 例外狀況提供兩個類別:  
  
-   處理的一般 OLE 例外狀況[COleException](../mfc/reference/coleexception-class.md)。  
  
-   產生和管理的 OLE 分派 \(自動\) 例外狀況[COleDispatchException](../mfc/reference/coledispatchexception-class.md)。  
  
 這兩個類別之間的差異在於它們，並提供的資訊量的地方使用它們。  `COleException` 不包含例外狀況的 OLE 狀態碼上的公用資料成員。  `COleDispatchException` 提供更多資訊，包括下列:  
  
-   一個應用程式相關的錯誤程式碼  
  
-   錯誤描述，例如「磁碟已滿」  
  
-   您的應用程式可用來為使用者提供額外資訊的說明內容  
  
-   您的應用程式中的說明檔案名稱  
  
-   造成例外狀況之應用程式或物件的名稱。  
  
 `COleDispatchException` 提供更多資訊，以便與 Microsoft Visual Basic 的產品。  用語錯誤描述可用於訊息方塊或其他通知;說明資訊可用來協助使用者回應造成例外狀況的條件。  
  
 兩個全域函式對應於兩個 OLE 例外狀況類別: [AfxThrowOleException](../Topic/AfxThrowOleException.md) 和 [AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md)。  使用它們分別擲回一般 OLE 例外狀況和 OLE 分派例外狀況。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)