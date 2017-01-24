---
title: "未預期是 &#39;(&#39; | Microsoft Docs"
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
  - "vbc32095"
  - "bc32095"
helpviewer_keywords: 
  - "BC32095"
ms.assetid: a47ad15a-2cfc-4d17-9012-27ba85b7d783
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未預期是 &#39;(&#39;
未預期是 '\('。 不允許未執行個體化的泛型類型陣列。  
  
 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法編譯陣列，除非它是特定資料類型。 您無法使用泛型類型的資料類型參數作為陣列的資料類型。  
  
 **錯誤 ID︰**BC32095  
  
### 更正這個錯誤  
  
-   如果您需要使用陣列，則必須將它宣告為特定資料類型。 您不能使用資料類型參數。  
  
-   如果您需要一組要提供給資料類型參數之資料類型的項目，則必須使用集合，而非陣列。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [NIB: Visual Basic 中的集合](http://msdn.microsoft.com/zh-tw/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)   
 [管理 Visual Basic 中的物件群組](http://msdn.microsoft.com/zh-tw/50be4910-4732-4d5f-a18a-055a162e9037)