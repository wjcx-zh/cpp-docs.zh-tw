---
title: "記錄捲動的命令處理常式 (MFC 資料存取) | Microsoft Docs"
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
  - "資料錄捲動 [C++]"
  - "資料錄檢視 [C++], 捲動"
  - "捲動資料錄"
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 記錄捲動的命令處理常式 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別 [CRecordView](../mfc/reference/crecordview-class.md) 和 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 為下列標準命令提供預設的命令處理：  
  
-   **ID\_RECORD\_MOVE\_FIRST**  
  
-   **ID\_RECORD\_MOVE\_LAST**  
  
-   **ID\_RECORD\_MOVE\_NEXT**  
  
-   **ID\_RECORD\_MOVE\_PREV**  
  
 類別 `CRecordView` 和 `CDaoRecordView` 的 `OnMove` 成員函式，提供所有在記錄間移動的四個命令的預設命令處理。  發出這些命令時，RFX \(或 DFX\) 會將新的記錄載入記錄集的欄位，DDX 則將值移到記錄表單的控制項中。  如需 RFX 的詳細資訊，請參閱[記錄欄位交換 \(RFX\)](../data/odbc/record-field-exchange-rfx.md)。  
  
> [!NOTE]
>  請務必為與標準記錄巡覽命令相關聯的任何使用者介面物件，使用這些標準命令 ID。  
  
## 請參閱  
 [支援資料錄檢視的巡覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)