---
title: "無法將 &#39;AddressOf&#39; 運算式轉換為 &#39;&lt;類型名稱&gt;&#39;，因為類型 &#39;&lt;類型名稱&gt;&#39; 宣告為 &#39;MustInherit&#39; 而且無法建立 | Microsoft Docs"
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
  - "vbc30939"
  - "bc30939"
helpviewer_keywords: 
  - "BC30939"
ms.assetid: e8edef15-0df5-46d7-aba6-89e26a2aa506
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;AddressOf&#39; 運算式轉換為 &#39;&lt;類型名稱&gt;&#39;，因為類型 &#39;&lt;類型名稱&gt;&#39; 宣告為 &#39;MustInherit&#39; 而且無法建立
陳述式會嘗試將 `AddressOf` 運算式轉換成只能是基底類別且不能用來建立執行個體的類型。  
  
 `AddressOf` 運算子會建立參考特定程序的程序委派執行個體。  
  
 **錯誤 ID︰**BC30939  
  
### 更正這個錯誤  
  
-   請將 `AddressOf` 運算式指派給特定委派類型。  
  
## 請參閱  
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegates](../Topic/Delegates%20\(Visual%20Basic\).md)