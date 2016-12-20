---
title: "不合法的呼叫運算式或索引運算式 | Microsoft Docs"
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
  - "vbc32303"
  - "bc32303"
helpviewer_keywords: 
  - "BC32303"
ms.assetid: eed6a16e-4a44-4f72-b1de-d4212940da37
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不合法的呼叫運算式或索引運算式
括弧中的值跟隨在非程序、屬性或陣列的運算式之後。  
  
 下列程式碼可能會產生此錯誤。  
  
 `Dim testVariable As Object = Nothing(1)`  
  
 因為 `Nothing` 不接受引數或索引，您不能使用括弧括住。  
  
 **錯誤 ID：**BC32303  
  
### 更正這個錯誤  
  
-   請移除括弧和內含的任何值。  
  
## 請參閱  
 [How to: Call a Procedure That Returns a Value](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)   
 [How to: Call a Procedure that Does Not Return a Value](../Topic/How%20to:%20Call%20a%20Procedure%20that%20Does%20Not%20Return%20a%20Value%20\(Visual%20Basic\).md)   
 [NOTINBUILD 如何：將值置入陣列](http://msdn.microsoft.com/zh-tw/6dddc79c-cf60-41c2-b572-8bfa49b4fe7e)   
 [NOTINBUILD 如何：從陣列取得值](http://msdn.microsoft.com/zh-tw/202a6468-8ccb-4864-bd8b-eab3b42d4288)   
 [How to: Put a Value in a Property](../Topic/How%20to:%20Put%20a%20Value%20in%20a%20Property%20\(Visual%20Basic\).md)   
 [How to: Get a Value from a Property](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)