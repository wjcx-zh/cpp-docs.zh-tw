---
title: "必須是 &#39;=&#39; (物件初始設定式) | Microsoft Docs"
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
  - "vbc30984"
  - "bc30984"
helpviewer_keywords: 
  - "BC30984"
ms.assetid: 9cae8d32-775a-414f-9e51-0469974b6aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;=&#39; (物件初始設定式)
若要在物件初始設定式宣告中建立欄位或屬性的初始值，您必須使用等號。 例如，下列宣告會指派 "Microsoft" 作為 `client` 之 `Name` 屬性的初始值。  
  
```  
Dim client As New Customer { .Name = "Microsoft" }  
```  
  
 **錯誤 ID︰**BC30984  
  
### 更正這個錯誤  
  
-   請在上述範例所顯示的位置中加入等號。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [不在組建中：屬性和屬性程序](http://msdn.microsoft.com/zh-tw/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [不在組建中：屬性程序與欄位](http://msdn.microsoft.com/zh-tw/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)