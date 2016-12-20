---
title: "執行階段類型資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RTTI 編譯器選項"
  - "執行階段, 類型檢查"
  - "執行階段檢查, 類型檢查"
  - "執行階段類型資訊"
  - "類型資訊, 執行階段類型檢查"
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 執行階段類型資訊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行階段類型資訊 \(RTTI\) 是一項機制，可在程式執行期間判斷物件的類型。  C\+\+ 語言中加入 RTTI 的原因在於，有許多類別庫的廠商本身實作這項功能。  這樣會導致程式庫之間不相容。  因此，在語言層級支援執行階段類型資訊的需求變得很明確。  
  
 為避免混淆，這裡討論的 RTTI 幾乎完全限於指標。  不過，所討論的概念也適用於參考。  
  
 執行階段類型資訊有三個主要的 C\+\+ 語言項目：  
  
-   [dynamic\_cast](../cpp/dynamic-cast-operator.md) 運算子。  
  
     用於多型類型的轉換。  
  
-   [typeid](../cpp/typeid-operator.md) 運算子。  
  
     用於識別物件的實際類型。  
  
-   [type\_info](../cpp/type-info-class.md) 類別。  
  
     用來保存 `typeid` 運算子傳回的類型資訊。  
  
## 請參閱  
 [轉型](../cpp/casting.md)