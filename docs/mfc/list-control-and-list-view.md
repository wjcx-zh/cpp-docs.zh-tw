---
title: "清單控制項和清單檢視 | Microsoft Docs"
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
  - "CListCtrl 類別, 和 CListView"
  - "CListView 類別, 和 CListCtrl"
  - "清單控制項, 清單檢視"
  - "清單檢視"
  - "檢視, 清單和清單控制項"
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 清單控制項和清單檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為了方便起見， 有兩種方式可以MFC 封裝清單控制項。  您可以使用清單控制項:  
  
-   直接透過內嵌 [CListCtrl](../mfc/reference/clistctrl-class.md) 物件在對話方塊類別。  
  
-   間接，使用 [CListView](../mfc/reference/clistview-class.md)類別。  
  
 表示 [CEditView](../mfc/reference/ceditview-class.md) 封裝編輯控制項，`CListView` 可整合 Project Server 與 MFC 文件\/檢視架構的清單控制項，封裝控制項:控制項填滿 MFC 檢視的整個介面。\(這個檢視 *是* 控制項，轉換為 `CListView`\)。  
  
 `CListView` 物件從 [CCtrlView](../mfc/reference/cctrlview-class.md) 和其基底類別繼承並加入成員函式以取得基礎清單控制項。  使用檢視成員與檢視當做檢視。  使用 [GetListCtrl](../Topic/CListView::GetListCtrl.md) 成員函式套用至清單控制項的成員函式存取。  使用這些成員:  
  
-   在清單中加入，刪除或操作「項目」。  
  
-   設定或取得清單控制項的屬性。  
  
 若要取得對基礎 `CListView`的 `CListCtrl` 的參考，請呼叫以清單檢視類別的 `GetListCtrl` :  
  
 [!code-cpp[NVC_MFCListView#4](../mfc/codesnippet/CPP/list-control-and-list-view_1.cpp)]  
  
 本主題會說明兩種使用清單控制項。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)