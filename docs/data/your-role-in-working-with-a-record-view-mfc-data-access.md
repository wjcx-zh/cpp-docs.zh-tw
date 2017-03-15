---
title: "您在使用記錄檢視上的角色 (MFC 資料存取) | Microsoft Docs"
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
  - "MFC, 資料錄檢視"
  - "資料錄檢視, 自訂預設程式碼"
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 您在使用記錄檢視上的角色 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您通常必須執行什麼操作才能使用資料錄檢視以及該架構為您執行什麼操作。  
  
### 使用資料錄檢視：您與架構  
  
|您|架構|  
|-------|--------|  
|使用 Visual C\+\+ 的話方塊編輯器來設計表單。|建立對話方塊樣板資源 \(含控制項\)。|  
|使用 [MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)， 建立從 [CRecordView](../mfc/reference/crecordview-class.md) 和 [CRecordset](../mfc/reference/crecordset-class.md) 或 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 和 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md) 衍生的類別。|為您撰寫類別。|  
|將資料錄檢視控制項對應至資料錄集欄位資料成員。|提供控制項與資料錄集欄位之間的 DDX。|  
||為功能表或工具列按鈕中的**最先移動**、**最後移動**、**移動下一個**和**移動前一個**命令提供預設命令處理常式。|  
||將變更更新到資料來源。|  
|\[選用\] 撰寫程式碼，以第二個資料錄集中的資料填入清單方塊或下拉式方塊或是其他控制項。||  
|\[選用\] 針對任何特殊驗證撰寫程式碼。||  
|\[選用\] 撰寫程式碼來加入或刪除資料錄。||  
  
 表單架構程式設計是唯一一個使用資料庫的方法。  如需使用一些其他使用者介面或無使用者介面的應用程式的詳細資訊，請參閱[MFC：使用具有文件和檢視的資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)和[MFC：使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。  如需顯示資料庫記錄的替代方法，請參閱類別 [CListView](../mfc/reference/clistview-class.md) 和 [CTreeView](../mfc/reference/ctreeview-class.md)。  
  
## 請參閱  
 [記錄檢視 \(MFC 資料存取\)](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)