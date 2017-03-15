---
title: "建立資料庫應用程式的作業順序 | Microsoft Docs"
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
  - "應用程式 [MFC], 資料庫"
  - "資料庫應用程式 [C++]"
  - "資料庫應用程式 [C++], 建立"
  - "MFC [C++], 資料庫應用程式"
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 建立資料庫應用程式的作業順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您的角色和架構的作用在文字資料庫應用程式。  
  
> [!NOTE]
>  從 Visual C\+\+ .NET 開始，Visual C\+\+ 環境和精靈不再支援 DAO \(但該版本中仍包含 DAO 類別，您仍然可以使用這些類別\)。  Microsoft 建議於新 MFC 專案使用 ODBC。  請在維護現有應用程式時再使用 DAO。  
  
### 建立資料庫應用程式  
  
|工作|您做|架構做|  
|--------|--------|---------|  
|決定是否要使用 MFC ODBC 或 DAO 類別。|請針對新的MFC專案使用 ODBC 。  使用 DAO 只維護現有應用程式。  參閱[我應該使用 DAO 或是 ODBC？](../data/should-i-use-dao-or-odbc-q.md) 如需一般資訊，請參閱本文件的 [資料存取程式設計](../data/data-access-programming-mfc-atl.md)。|這個架構提供支援資料庫存取的類別。|  
|建立使用資料庫選項的基本架構應用程式。|執行 MFC 應用程式精靈。  選取資料庫支援頁面上的選項。  如果您選擇要建立資料錄檢視的選項，請指定:<br /><br /> -   資料來源和資料表名稱或名稱<br />-   查詢名稱或名稱。|MFC 應用程式精靈建立檔案並指定必要包括。  根據指定的選項，檔案中包含資料錄集類別。|  
|設計您的資料庫資料表或表單。|使用 Visual C\+\+ 對話方塊編輯器將控制項放置在您的資料錄檢視類別的對話方塊範本資源。|MFC 應用程式精靈為您建立空白對話方塊樣板資源可以填入。|  
|建立附加記錄檢視和資料錄集類別的需要。|使用類別檢視建立類別和對話方塊編輯器設計檢視。|類別檢視建立新類別的其他檔案。|  
|建立資料錄集物件視需要在您的程式碼。  使用每個資料錄集操作資料錄…|您的資料錄集根據精靈的 [CRecordset](../mfc/reference/crecordset-class.md) 衍生的類別。|ODBC 使用資料錄欄位交換 \(RFX\) 至資料庫和資料錄集的欄位資料成員間交換資料。  如果您使用資料錄檢視，資料錄集和控制項之間的對話資料交換 \(Dialog Data Exchange，DDX\) 交換資料在這個資料錄檢視。|  
|…或建立明確 [CDatabase](../mfc/reference/cdatabase-class.md) 以您要開啟的每個資料庫的程式碼。|根據您的資料錄集物件的資料庫物件。|資料庫物件提供資料來源。|  
|資料錄集：動態地繫結資料行 \(ODBC\)。|在 ODBC，對您的處理繫結的衍生資料錄集類別內加入程式碼。  請參閱文章[資料錄集：動態地繫結資料行 \(ODBC\)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||  
  
## 請參閱  
 [在架構上建置](../mfc/building-on-the-framework.md)   
 [建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)