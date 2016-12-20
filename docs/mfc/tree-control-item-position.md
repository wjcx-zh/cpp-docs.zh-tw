---
title: "樹狀目錄控制項目位置 | Microsoft Docs"
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
  - "CTreeCtrl 類別, 項目位置"
  - "樹狀目錄控制項中的項目位置"
  - "位置, CTreeCtrl 項目"
  - "樹狀目錄控制項, 項目位置"
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 樹狀目錄控制項目位置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

項目的初始位置設定，將項目加入至樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 時使用 `InsertItem` 成員函式。  成員函式呼叫指定父項目的控制代碼和項目的控制代碼，之後要插入新的項目。  第二個控制代碼必須識別任何子項目指定父代或一個值: `TVI_FIRST`、 `TVI_LAST`或 `TVI_SORT`。  
  
 當 `TVI_FIRST` 或 `TVI_LAST` 時，樹狀目錄控制項放置在新項目或結尾的子項目指定父項目的清單。  當 `TVI_SORT` 指定時，樹狀目錄控制項以字母順序插入新的項目根據項目標籤文字的子項目清單。  
  
 您可以將子項目的項目清單輸入字母順序會藉由呼叫 [SortChildren](../Topic/CTreeCtrl::SortChildren.md) 成員函式。  這個函式包含指定的參數所有層級深度之父項目的子項目是否以字母順序來排序。  
  
 [SortChildrenCB](../Topic/CTreeCtrl::SortChildrenCB.md) 成員函式可讓您排序依據您所定義的準則的子項目。  當您呼叫這個函式時，您指定樹狀目錄控制項有樣式的應用程式定義的回呼函式，只要兩個子項目相對順序所決定。  您指定，當呼叫 `SortChildrenCB`時的回呼函式接收所比較之項目的兩個 32 位元應用程式定義的值和第三個 32 位元值。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)