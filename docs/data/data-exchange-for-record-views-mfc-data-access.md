---
title: "記錄檢視的資料交換 (MFC 資料存取) | Microsoft Docs"
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
  - "DDX (對話資料交換), 資料錄檢視"
  - "DFX (DAO 資料錄欄位交換)"
  - "DFX (DAO 資料錄欄位交換), 資料交換機制"
  - "DFX (DAO 資料錄欄位交換), 資料錄檢視"
  - "資料錄檢視, 資料交換"
  - "RFX (資料錄欄位交換)"
  - "RFX (資料錄欄位交換), 資料交換機制"
  - "RFX (資料錄欄位交換), 資料錄檢視"
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 記錄檢視的資料交換 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用[加入類別](../mfc/reference/adding-an-mfc-odbc-consumer.md)將記錄檢視的對話方塊範本資源中的控制項對應至記錄集的欄位時，架構會管理雙向的資料交換 — 從記錄集到控制項，以及從控制項到記錄集。  使用 DDX 機制意味著您不需要自行撰寫程式碼以來回傳輸資料。  
  
 記錄檢視的 DDX 可搭配下列項目一起運作：  
  
-   類別 `CRecordset` \(ODBC\) 之記錄集的 [RFX](../data/odbc/record-field-exchange-rfx.md)。  
  
-   類別 `CDaoRecordset` \(DAO\) 之記錄集的 DFX。  
  
 雖然它們在實作時有差異，但在介面層級的 RFX 和 DFX 是非常類似的資料交換機制。  DAO 版本的 DFX 是以先前的 ODBC 版本 RFX 做為藍本。  如果您知道如何使用 RFX，就會知道如何使用 DFX。  
  
 RFX 和 DFX 會在資料來源的目前記錄，以及記錄集物件的欄位資料成員之間移動資料。  DDX 會將資料，從欄位資料成員移到表單中的控制項。  這種組合會在一開始以及使用者在記錄間移動時，填滿表單控制項。  它也可以將更新的資料移動回記錄集，然後移到資料來源。  
  
 下圖顯示記錄檢視的 DDX 及 RFX \(或 DFX\) 之間的關係。  
  
 ![對話方塊資料交換和資料錄欄位交換](../data/media/vc37xt1.png "vc37XT1")  
對話方塊資料交換及記錄欄位交換  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。  如需 RFX 的詳細資訊，請參閱[記錄欄位交換 \(RFX\)](../data/odbc/record-field-exchange-rfx.md)。  
  
## 請參閱  
 [記錄檢視 \(MFC 資料存取\)](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)