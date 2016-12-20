---
title: "記錄檢視的使用者介面更新 (MFC 資料存取) | Microsoft Docs"
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
  - "功能表, 更新為內容變更"
  - "資料錄檢視, 使用者介面"
  - "使用者介面, 更新"
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 記錄檢視的使用者介面更新 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CRecordView` 和 `CDaoRecordView` 也提供巡覽命令的預設使用者介面更新處理常式。  這些處理常式會自動啟用和停用功能表項目和工具列按鈕等使用者介面物件。  應用程式精靈提供標準功能表，而如果您選擇**可停駐工具列**選項，則會提供一組命令工具列按鈕。  如果您使用 `CRecordView` 建立記錄檢視類別，可能需要將類似的使用者介面物件加入應用程式。  
  
### 使用功能表編輯器建立功能表資源  
  
1.  請參閱使用[功能表編輯器](../mfc/menu-editor.md)的詳細資訊，以相同的四個命令建立您自己的功能表。  
  
#### 使用圖形編輯器建立工具列按鈕  
  
1.  請參閱使用[工具列編輯器](../mfc/toolbar-editor.md)的詳細資訊，編輯工具列資源以加入記錄巡覽命令的工具列按鈕。  
  
## 請參閱  
 [支援資料錄檢視的巡覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)