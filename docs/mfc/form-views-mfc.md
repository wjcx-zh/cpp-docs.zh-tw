---
title: "表單檢視 (MFC) | Microsoft Docs"
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
  - "應用程式 [MFC], 表單架構"
  - "表單 [C++]"
  - "表單 [C++], 加入至應用程式"
  - "表單架構應用程式"
  - "使用者介面, 表單"
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 表單檢視 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以將表單加入至支援 MFC 程式庫的所有 Visual C\+\+ 應用程式，包括 [表單架構應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md) \(檢視類別衍生自 `CFormView`\) 的物件。  如果您原本沒有建置應用程式支援表單， Visual C\+\+ 會將此備份，在插入新的表單。  在 SDI 或 MDI 應用程式中，實作預設的 [文件\/檢視架構](../mfc/document-view-architecture.md)，，當使用者選取 `New` 命令 \(根據預設，在檔案功能表\)， Visual C\+\+ 會提示使用者從可用的表單選取。  
  
 SDI 應用程式，也就是說，當使用者選取 `New` 命令時，表單的目前執行個體繼續執行，但應用程式建立新的執行個體與選取的表單的建立，如果沒有找到物件。  在 MDI 應用程式，也就是說，當使用者選取 `New` 命令時，表單的目前執行個體繼續執行。  
  
> [!NOTE]
>  您可以插入表單的對話方塊架構應用程式 \(對話方塊類別根據 `CDialog` 檢視類別未實作\) 的其中一個。  不過，不具有文件\/檢視架構， Visual C\+\+ 不自動實作 **File** &#124;\[**新增**\] 功能。  您必須建立使用者的一個方式來檢視其他表單，例如藉由實作成索引標籤式對話方塊以各種不同的屬性頁。  
  
 當您將新的表單至應用程式時， Visual C\+\+ 執行下列動作:  
  
-   根據您選擇的其中一個類別表單式類別 \(`CFormView`、 `CRecordView`、 `CDaoRecordView`或 `CDialog`\)。  
  
-   會以適當的樣式 \(或您的對話方塊資源能使用未與類別\) 的現有的對話方塊資源。  
  
     如果您選取現有的對話方塊資源，使用對話方塊的屬性頁，您可能必須將這些樣式。  對話方塊的樣式必須包括:  
  
     **WS\_CHILD**\=On  
  
     `WS_BORDER`\=Off  
  
     **WS\_VISIBLE**\=Off  
  
     **WS\_CAPTION\=**  
  
 以文件\/檢視架構也的應用程式， **New Form** 命令 \(以滑鼠右鍵按一下在類別檢視中\):  
  
-   建立 **CDocument**架構類別  
  
     而不會有一個名為的新類別建立，您可以使用任何現有 **CDocument**\-在專案的基底類別。  
  
-   產生文件樣板 \(衍生自 **CDocument**\) 有字串、功能表和圖示資源的。  
  
     您也可以根據範本建立新的類別。  
  
-   將呼叫加入至 **AddDocumentTemplate** 以您的應用程式程式碼的 `InitInstance` 。  
  
     Visual C\+\+ 將您建立的，將表單加入至可用的表單清單的每個新表單的程式碼，在使用者選取 `New` 命令時。  這個程式碼加入表單的關聯的資源 ID 和一起構成新表單物件相關聯的文件、檢視和架構類別的名稱。  
  
     文件樣板做為文件框架視窗與檢視之間的連接。  對於單一文件，您可以建立許多範本。  
  
 如需詳細資訊，請參閱：  
  
-   [建立表單架構應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [插入表單的專案](../mfc/inserting-a-form-into-a-project.md)  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)