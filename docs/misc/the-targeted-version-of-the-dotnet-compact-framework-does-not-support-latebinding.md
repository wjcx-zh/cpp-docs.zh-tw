---
title: ".NET Compact Framework 的目標版本不支援晚期繫結 | Microsoft Docs"
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
  - "vbc30762"
  - "bc30762"
helpviewer_keywords: 
  - "BC30762"
ms.assetid: b433014d-8422-46e8-ad55-321146a48186
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# .NET Compact Framework 的目標版本不支援晚期繫結
您使用的 .NET Compact Framework 版本不支援晚期繫結。  
  
 **錯誤 ID︰**BC30762  
  
### 更正這個錯誤  
  
1.  避免在宣告為物件的變數上呼叫函式、Sub 或屬性。  
  
2.  避免將物件變數當做陣列使用。  
  
3.  避免搭配物件變數使用字典成員存取運算式。  
  
## 請參閱  
 [NotInBuild：Visual Basic 中的物件](http://msdn.microsoft.com/zh-tw/85bd757a-a19e-45e1-af89-d68765f5ee3c)   
 [Special Characters in Code](../Topic/Special%20Characters%20in%20Code%20\(Visual%20Basic\).md)