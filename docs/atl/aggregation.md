---
title: "Aggregation | Microsoft Docs"
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
  - "aggregate objects [C++]"
  - "aggregation [C++]"
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Aggregation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有時候，當物件的實作器要使用類別所提供的服務，預先建置的物件。  此外，它也希望這第二個物件會顯示為一個自然區段中的第一個。  COM 透過內含項目和彙總達成這兩個目標。  
  
 彙總表示包含 \(以外\) 物件建立內含 \(內部\) 物件當做它的建立過程中，而內部物件的介面是由外部公開。  物件允許本身 aggregatable。  如果是，則它必須遵循彙總的規則可以正常運作。  
  
 通常，在內含物件的所有 **IUnknown** 方法呼叫都必須委派加入包含的物件。  
  
## 請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [Reusing Objects](http://msdn.microsoft.com/library/windows/desktop/ms678443)