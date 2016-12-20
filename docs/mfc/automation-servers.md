---
title: "Automation 伺服程式 | Microsoft Docs"
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
  - "Automation 伺服程式"
  - "COM 元件, Automation 伺服程式"
  - "分派對應, Automation 伺服程式"
  - "伺服器, Automation"
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Automation 伺服程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Automation 可讓您的應用程式可以操作在另一個應用程式實作的物件，或者公開物件，因此可以操作。  Automation 伺服程式是公開可程式化物件的應用程式呼叫 \(Automation 物件\) 到其他應用程式 \(稱為 [Automation 用戶端](../mfc/automation-clients.md)\)。  Automation 伺服程式有時稱為 Automation 元件。  
  
 公開 Automation 物件使用戶端可以直接存取物件自動化某些程序，而功能伺服器所提供。  公開物件以這種方式有用處，當應用程式提供其他應用程式很有用的功能。  例如，文書處理器可能會公開其拼字檢查功能，讓其他程式可以使用它。  使用其他應用程式的現成的功能，使物件公開廠商改善其應用程式的功能。  
  
 這些 Automation 物件具有的屬性與方法做為其外部介面。  屬性是 Automation 物件的名稱屬性。  屬性與 C \+\+. 類別的資料成員。  方法是在 Automation 物件運作的函式。  方法類似 C \+\+ 類別的公用成員函式。  
  
> [!NOTE]
>  雖然屬性是像 C\+\+ 資料成員，就無法直接存取的。  若要提供透明的存取，請在 Automation 物件的內部變數以取得\/設定成員函式存取它們。  
  
 透過公開應用程式功能可以共用，明確定義的介面，在 Automation \(如 Microsoft Visual Basic 的單一一般程式語言可以用來建立應用程式而不是在不同，應用程式專屬巨集語言存取。  
  
##  <a name="_core_support_for_automation_servers"></a> 支援 Automation 伺服程式  
 Visual C\+\+ 和 MFC 架構的 Automation 伺服程式提供廣泛的支援。  這些處理做 Automation 伺服程式的許多額外負荷，因此，您可以將您的工作於應用程式的功能。  
  
 支援的 Automation 架構的主要機制是分派對應，展開成宣告及呼叫需要公開方法和屬性 OLE 的一組巨集。  典型的分派對應如下所示:  
  
 [!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/CPP/automation-servers_1.cpp)]  
  
 屬性視窗和類別檢視協助維護的分派對應。  當您將新的方法或屬性加入至類別時， Visual C\+\+ 會將對應的 `DISP_FUNCTION` 或 `DISP_PROPERTY` 巨集與表示類別名稱、方法的外部和內部名稱的參數或屬性和資料型別。  
  
 **Add Class** 對話方塊也簡化了 Automation 類別及其屬性和作業的管理的宣告。  當您使用加入類別\] 對話方塊將類別加入至專案時，您會指定它的基底類別。  如果基底類別允許 Automation，使用指定的加入類別\] 對話方塊中顯示控制項新的類別是否應支援 Automation，它是否「OLE」\(可建立類別的物件即是否在從 COM 用戶端的要求可以建立\) 和外部名稱對於 COM 用戶端使用。  
  
 **Add Class** 對話方塊會建立一個類別宣告，包括您指定的 OLE 功能的適當的巨集。  它也會將類別成員函式的實作基本架構程式碼。  
  
 MFC 應用程式精靈簡化在取得您的 Automation 伺服器應用程式所需的步驟間接。  如果您選取 **Automation** 核取方塊從 \[**進階功能**\] 頁， MFC 應用程式精靈將加入至應用程式的 `InitInstance` 函式所需的呼叫註冊 Automation 物件並執行您的應用程式當做 Automation 伺服程式。  
  
### 您想要執行甚麼工作？  
  
-   [了解 Automation 用戶端](../mfc/automation-clients.md)  
  
-   [進一步了解類別 CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
  
-   [進一步了解類別 COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)  
  
## 請參閱  
 [Automation](../mfc/automation.md)   
 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)