---
title: "初始化的欄位或屬性，其名稱開頭必須是 &#39;.&#39; | Microsoft Docs"
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
  - "vbc30985"
  - "bc30985"
helpviewer_keywords: 
  - "BC30985"
ms.assetid: 4cb543e1-477c-429c-82df-541ebff08543
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 初始化的欄位或屬性，其名稱開頭必須是 &#39;.&#39;
物件初始設定式清單中的每個成員初始設定式會指定欄位或屬性的名稱和其初始值。 欄位或屬性的名稱前面必須加上句號。 例如，下列宣告會指派 "Microsoft" 作為 `client` 之 `Name` 屬性的初始值。  
  
```  
Dim client As New Customer() With { .Name = "Microsoft" }  
```  
  
 **錯誤 ID︰**BC30985  
  
### 更正這個錯誤  
  
-   請在每個成員名稱前面加上句號。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [不在組建中：屬性程序與欄位](http://msdn.microsoft.com/zh-tw/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)