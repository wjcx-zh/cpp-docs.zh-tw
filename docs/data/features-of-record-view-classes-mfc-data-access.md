---
title: "記錄檢視類別的功能 (MFC 資料存取) | Microsoft Docs"
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
  - "資料錄檢視類別"
  - "資料錄檢視, 類別"
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 記錄檢視類別的功能 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用類別 [CFormView](../mfc/reference/cformview-class.md) 進行表單架構的資料存取程式設計，但通常 [CRecordView](../mfc/reference/crecordview-class.md) 和 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 是更好的衍生類別。  除了其 `CFormView` 功能外，`CRecordView` 和 `CDaoRecordView` 還可以：  
  
-   提供表單控制項和相關聯記錄集物件之間的對話資料交換 \(DDX\)。  
  
-   處理移到最前面、移到下一個、移到上一個及移到最後面的命令，以巡覽關聯記錄集物件中的記錄。  
  
-   當使用者移到另一筆記錄時，更新會變更為目前的記錄。  
  
 如需有關巡覽的詳細資訊，請參閱[記錄檢視：支援記錄檢視的巡覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)。  
  
## 請參閱  
 [記錄檢視 \(MFC 資料存取\)](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)