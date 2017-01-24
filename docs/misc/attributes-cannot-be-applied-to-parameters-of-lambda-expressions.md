---
title: "無法將屬性套用至 Lambda 運算式的參數 | Microsoft Docs"
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
  - "vbc36634"
  - "bc36634"
helpviewer_keywords: 
  - "BC36634"
ms.assetid: ed751d8d-11b7-4210-97e0-0319edff8c34
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將屬性套用至 Lambda 運算式的參數
您已將屬性套用至 Lambda 運算式定義中的參數，不支援這麼做。 下列程式碼會產生這個錯誤。  
  
```vb#  
Sub LambaAttribute()  
    ' Not valid.  
    Dim add1 = _  
    Function(<System.Runtime.InteropServices.InAttribute()> m As Integer) _  
                   m + 1  
End Sub  
```  
  
 **錯誤 ID︰**BC36634  
  
### 更正這個錯誤  
  
-   請移除屬性，或考慮修改程式碼，將 Lambda 運算式變更為一般函式。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.InAttribute>   
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)