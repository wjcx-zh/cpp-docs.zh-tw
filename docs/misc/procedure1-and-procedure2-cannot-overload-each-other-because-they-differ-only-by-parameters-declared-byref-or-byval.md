---
title: "&#39;&lt;程序1&gt;&#39; 和 &#39;&lt;程序2&gt;&#39; 無法互相多載，因為它們的差異只在於宣告為 &#39;ByRef&#39; 或 &#39;ByVal&#39; 的參數不同而已 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42003"
  - "bc42003"
helpviewer_keywords: 
  - "BC42003"
ms.assetid: f058f1e0-64d2-4497-85fc-a58e16b0d805
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;程序1&gt;&#39; 和 &#39;&lt;程序2&gt;&#39; 無法互相多載，因為它們的差異只在於宣告為 &#39;ByRef&#39; 或 &#39;ByVal&#39; 的參數不同而已
'\<程序1\>' 和 '\<程序2\>' 無法互相多載，因為它們的差異只在於宣告為 ByRef 或 ByVal 的參數不同而已。 假設為遮蔽。  
  
 這兩種程序宣告指定相同的名稱和引數清單，而唯一的差別在於一或多個引數的 `ByRef` 或 `ByVal` 指定。 程序的多載版本必須在引數的數目、順序或資料類型方面與彼此不同。  
  
 這個訊息是一個警告。 預設會假設為 `Shadows`。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42003  
  
### 更正這個錯誤  
  
-   如果您想要建立程序的一組多載版本，請讓每版本中的引數數目、順序或資料類型不同。 此外，也請將 `Overloads` 關鍵字加入每個宣告中。  
  
-   如果您不想多載程序，請變更其中一個宣告中的程序名稱。  
  
## 請參閱  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)