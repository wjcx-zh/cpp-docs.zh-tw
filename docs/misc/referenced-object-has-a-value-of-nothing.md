---
title: "參考的物件具有 &#39;Nothing&#39; 的值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30760"
  - "vbc30760"
helpviewer_keywords: 
  - "BC30760"
ms.assetid: 7e792fd8-2880-402b-a908-c89e5b028300
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 參考的物件具有 &#39;Nothing&#39; 的值
正在使用的物件具有值 `Nothing`，但必須是可使用的值。`Nothing` 是一個值，表示物件沒有值，這可能是因為尚未指定任何值給它，或它被指派值 `Nothing`。  
  
 **錯誤 ID︰**BC30760  
  
### 更正這個錯誤  
  
1.  請檢查物件，並確定它已在發生錯誤的程序範圍內宣告。  
  
2.  確認要設定之物件的值。  
  
    > [!NOTE]
    >  值 `Nothing` 不為零或空字串。 您可以使用 `IsNothing` 來檢查物件是否包含值 `Nothing`。  
  
## 請參閱  
 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)   
 [不在組建中：IsNothing 函式](http://msdn.microsoft.com/zh-tw/5b2a4626-e6a9-49d1-b9b1-fcc6a1302319)