---
title: "Option Strict On 不允許晚期繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 不允許晚期繫結
[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 允許將任何資料類型隱含地轉換成任何其他資料類型。 不過，如果將某種資料類型的值轉換成精確度較低或容量較小的資料類型，則資料可能會遺失。`Option Strict On` 可確保這些類型之轉換的編譯時期通知，因而予以避免。 您不能使用具有晚期繫結的 `Option Strict On`。  
  
 下列程式碼範例會使用晚期繫結，並在 `Option Strict` 設為 `On` 時造成這個錯誤。  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **錯誤 ID︰**BC30574  
  
### 更正這個錯誤  
  
-   請修改物件宣告，以使用明確類型 \(如下列範例所示\)：  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 \-或\-  
  
-   請修改晚期繫結運算式，以指定明確類型 \(如下列範例所示\)：  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 \-或\-  
  
-   請讓編譯器推斷特定類型 \(如下列範例所示\)：  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 \-或\-  
  
-   移除其後的 `On` 這個字，或明確指定 `Off`，以關閉 `Option Strict`。  
  
## 請參閱  
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)   
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)