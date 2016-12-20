---
title: "指派轉換 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "指派轉換"
  - "轉換, 設定"
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 指派轉換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在指派運算中，將指派值的類型會轉換成接收指派的變數類型。  C 可藉由指派而在整數和浮點類型之間轉換，即使資訊會在轉換過程中遺失。  使用的轉換方法取決於指派時採用的類型，如[一般算術轉換](../c-language/usual-arithmetic-conversions.md)以及下列各節中所述：  
  
-   [從帶正負號的整數類型轉換](../c-language/conversions-from-signed-integral-types.md)  
  
-   [從不帶正負號的整數類型轉換](../c-language/conversions-from-unsigned-integral-types.md)  
  
-   [從浮點類型轉換](../c-language/conversions-from-floating-point-types.md)  
  
-   [指標類型的相互轉換](../c-language/conversions-to-and-from-pointer-types.md)  
  
-   [從其他類型轉換](../c-language/conversions-from-other-types.md)  
  
 類型限定詞不會影響轉換的允許值，雖然 **const** 左值不可以在指派的左邊使用。  
  
## 請參閱  
 [類型轉換](../c-language/type-conversions-c.md)