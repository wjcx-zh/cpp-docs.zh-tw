---
title: "將控制項加入至屬性工作表 | Microsoft Docs"
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
  - "控制項 [MFC], 加入至屬性工作表"
  - "屬性工作表, 加入控制項"
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將控制項加入至屬性工作表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，屬性工作表配置屬性頁、索引標籤和判斷、移除和應用程式按鈕的視窗區域。\(非強制回應的屬性工作表沒有確定按鈕, 取消按鈕, 套用按鈕\)。您可以將其他控制項加入至屬性工作表。  例如，如果套用至外部物件您可以在屬性頁區域右邊加入預覽視窗會顯示選取控制項中目前設定的外觀。  
  
 您可以加入控制項至 `OnCreate` 處理常式的屬性工作表對話方塊。  包容的其他控制項通常需要展開屬性工作表對話方塊的大小。  在呼叫基底類別 \( **CPropertySheet::OnCreate**之後，呼叫 [GetWindowRect](../Topic/CWnd::GetWindowRect.md) 取得寬度和高度配置的屬性工作表視窗，目前展開矩形的維度，然後呼叫 [MoveWindow](../Topic/CWnd::MoveWindow.md) 變更屬性工作表視窗的大小。  
  
## 請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)   
 [CPropertyPage Class](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet Class](../mfc/reference/cpropertysheet-class.md)