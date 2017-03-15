---
title: "將資料行加入至控制項 (報表檢視) | Microsoft Docs"
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
  - "CListCtrl 類別, 加入資料行"
  - "CListCtrl 類別, 報表檢視"
  - "資料行 [C++], 加入至 CListCtrl"
  - "CListCtrl 類別中的報表檢視"
  - "檢視, 報告"
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 將資料行加入至控制項 (報表檢視)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列程序適用於 [CListView](../mfc/reference/clistview-class.md) 或 [CListCtrl](../mfc/reference/clistctrl-class.md) 物件。  
  
 當清單控制項在報表檢視時，會顯示提供組織每個清單項目控制項各種項目方法。  這個組織實作具有一列在清單控制項和清單控制項項目的關聯的子項目之間有一對一的對應。  如需子項目的詳細資訊，請參閱 [將項目加入控制項](../mfc/adding-items-to-the-control.md)。  清單控制項的範例在報表檢視中由在 Windows 95 和 Windows 98 總管的詳細資料檢視中提供。  第一欄列出資料夾、檔案圖示和標籤。  其他資料行清單檔案大小，檔案類型，最後更新日期，依此類推。  
  
 即使資料行可以隨時加入到清單控制項，資料行為可見，只有在控制項將裝置的 `LVS_REPORT` 樣式位元時。  
  
 每個資料列都有相關聯的標頭項目 \(請參閱 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) 物件標記行並允許使用者調整資料列大小。  
  
 如果您的清單控制項支援報告檢視，您必須將每個可能的子項目的資料行清單控制項項目。  您可以準備 [LV\_COLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743) 結構然後呼叫將資料行加入至 [InsertColumn](../Topic/CListCtrl::InsertColumn.md)。  在加入必要的資料行之後 \(有時稱為標題項目\)，您可以重新排列它們使用屬於內嵌標題控制項的成員函式和樣式。  如需詳細資訊，請參閱 [在標題控制項的排序項目。](../mfc/ordering-items-in-the-header-control.md)。  
  
> [!NOTE]
>  如果清單控制項建立與 **LVS\_NOCOLUMNHEADER** 樣式時，任何嘗試插入資料列會被忽略。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)