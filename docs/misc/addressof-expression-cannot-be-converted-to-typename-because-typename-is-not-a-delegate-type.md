---
title: "&#39;AddressOf&#39; 運算式不可以轉換成 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;&lt;類型名稱&gt;&#39; 不是委派類型 | Microsoft Docs"
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
  - "vbc30581"
  - "bc30581"
helpviewer_keywords: 
  - "BC30581"
ms.assetid: 5db7589a-5456-4b3a-9d6b-93d9157f0484
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddressOf&#39; 運算式不可以轉換成 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;&lt;類型名稱&gt;&#39; 不是委派類型
陳述式嘗試將 `AddressOf` 運算式轉換為非委派類型的類型。  
  
 `AddressOf` 運算子會建立參考特定程序的程序委派執行個體。`AddressOf` 可以當做委派建構函式的運算元使用，也可以用於由編譯器決定委派類型的內容中。  
  
 **錯誤 ID︰**BC30581  
  
### 更正這個錯誤  
  
-   將目標類型變更為委派類型。  
  
## 請參閱  
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)