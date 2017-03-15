---
title: "基底類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基底類別"
  - "基底類別, 虛擬"
  - "衍生類別, 多個基底"
  - "繼承, 多個"
  - "多重繼承, 基底類別"
  - "虛擬基底類別"
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 基底類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

繼承的程序會建立新的衍生類別，該類別是由基底類別的成員再加上由衍生類別加入的任何新成員所組成。  在多重繼承中可以建構繼承圖形，其中相同的基底類別是屬於多個衍生類別的一部分。  下圖顯示這類圖形。  
  
 ![單一基底類別的多個執行個體](../cpp/media/vc38xn1.png "vc38XN1")  
單一基底類別的多個執行個體  
  
 圖中以圖示表示 `CollectibleString` 和 `CollectibleSortable` 的各個元件。  不過，位於 `Collectible` 中的基底類別 `CollectibleSortableString` 是透過 `CollectibleString` 路徑和 `CollectibleSortable` 路徑存取。  若要消除這種冗餘狀況，可以在繼承時將這些類別宣告為虛擬基底類別。  
  
 如需宣告虛擬基底類別，以及具有虛擬基底類別物件之組合方式的詳細資訊，請參閱[虛擬基底類別](../misc/virtual-base-classes.md)。  
  
## 請參閱  
 [衍生類別概觀](../misc/overview-of-derived-classes.md)