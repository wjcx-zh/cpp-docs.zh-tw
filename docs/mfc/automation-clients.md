---
title: "Automation 用戶端 | Microsoft Docs"
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
  - "Automation 用戶端"
  - "用戶端"
  - "用戶端, Automation"
  - "類型程式庫, Automation 用戶端"
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Automation 用戶端
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Automation 可讓您的應用程式可以操作在另一個應用程式實作的物件，或者公開物件，因此可以操作。  Automation 用戶端可以操作屬於另一個應用程式的已公開物件的應用程式。  公開物件的應用程式呼叫 Automation 伺服程式。  用戶端可以存取其屬性和函式管理伺服器應用程式的物件。  
  
### Automation 用戶端的型別  
 用戶端自動化有兩種：  
  
-   的用戶端 \(在執行階段\) 以動態方式取得與伺服器的屬性和作業的相關資訊。  
  
-   擁有靜態資訊的用戶端 \(提供在編譯時期\) 指定伺服器的屬性和作業。  
  
 第一個類型取得資訊的用戶端與伺服器的方法和屬性可以藉由查詢 OLE 系統的 `IDispatch` 機制。  雖然它是完整為動態用戶端使用 `IDispatch` ，很難為靜態用戶端使用，必須知道要巡覽的物件在編譯時期。  對於靜態繫結的用戶端， MFC 提供 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) 類別。  
  
 靜態繫結用戶端用來與用戶端應用程式靜態連結的 Proxy 類別。  這個類別提供伺服器應用程式的屬性和作業的型別安全 C\+\+ 套件。  
  
 類別 `COleDispatchDriver` 為 Automation 用戶端提供主要支援。  使用 `Add New Item` 對話方塊，您可以建立衍生自 `COleDispatchDriver`的類別。  
  
 然後指定描述伺服器應用程式的物件的屬性和函式的型別程式庫檔案。  加入項目對話方塊中讀取這個檔案並建立 `COleDispatchDriver`衍生類別，與成員函式應用程式可以呼叫存取在 C\+\+ 的伺服器應用程式的物件提供型別安全方式。  繼承自 `COleDispatchDriver` 的其他功能簡化呼叫適當的 Automation 伺服程式流程。  
  
### 在 Automation 用戶端處理事件  
 如果您要處理您的 Automation 用戶端事件，您必須將接收介面。  MFC 提供精靈不是供加接收介面為 ActiveX 控制項，不過，支援其他 COM 伺服器。  如需如何將 MFC 用戶端的接收介面的 COM 伺服器資訊描述的來源介面的詳細資訊，請參閱 HOWTO:建立在 MFC 架構的 COM 用戶端 \(181845 KB\) 之接收介面中 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;181845](http://support.microsoft.com/default.aspx?scid=kb;en-us;181845)。  
  
## 請參閱  
 [Automation 用戶端：使用類型程式庫](../mfc/automation-clients-using-type-libraries.md)   
 [Automation](../mfc/automation.md)   
 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)