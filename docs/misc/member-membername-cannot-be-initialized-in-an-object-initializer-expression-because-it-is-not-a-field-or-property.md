---
title: "成員 &#39;&lt;成員名稱&gt;&#39; 無法在物件初始設定式運算式中初始化，它不是欄位或屬性 | Microsoft Docs"
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
  - "bc30990"
  - "vbc30990"
helpviewer_keywords: 
  - "BC30990"
ms.assetid: 3be2c135-20f6-49b2-a324-d213cfdf9ee3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 成員 &#39;&lt;成員名稱&gt;&#39; 無法在物件初始設定式運算式中初始化，它不是欄位或屬性
物件初始設定式清單不能包括共用成員、常數或方法呼叫。 初始設定式清單中的成員必須是欄位或屬性，而且屬性成員不需要引數。  
  
 **錯誤 ID︰**BC30990  
  
### 更正這個錯誤  
  
-   請從物件初始設定式清單中移除所有共用成員、常數、方法呼叫或具有參數的屬性。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [不在組建中：Visual Basic 中的共用成員](http://msdn.microsoft.com/zh-tw/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [不在組建中：屬性和屬性程序](http://msdn.microsoft.com/zh-tw/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [不在組建中：預設屬性](http://msdn.microsoft.com/zh-tw/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NotInBuild：物件成員](http://msdn.microsoft.com/zh-tw/dfc2cc12-0e66-44fb-a78e-14f931db2309)   
 [Const Statement](../Topic/Const%20Statement%20\(Visual%20Basic\).md)