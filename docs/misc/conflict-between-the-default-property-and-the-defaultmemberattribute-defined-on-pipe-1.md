---
title: "預設屬性與 &#39;|1&#39; 上定義的 &#39;DefaultMemberAttribute&#39; 相衝突 | Microsoft Docs"
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
  - "vbc32304"
  - "bc32304"
helpviewer_keywords: 
  - "BC32304"
ms.assetid: 42803d13-ff1d-40ed-a4a8-269e2fb4aa01
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 預設屬性與 &#39;|1&#39; 上定義的 &#39;DefaultMemberAttribute&#39; 相衝突
類別、結構或介面使用 [Default](../Topic/Default%20\(Visual%20Basic\).md) 關鍵字來宣告預設屬性，但也套用 <xref:System.Reflection.DefaultMemberAttribute> 以將不同的成員指定為預設成員。  
  
 類型最多可以有一個預設成員。 當您宣告預設屬性時，Visual Basic 會將 <xref:System.Reflection.DefaultMemberAttribute> 自動套用至指定該屬性的類別、結構或介面。  
  
 **錯誤 ID︰**BC32304  
  
### 更正這個錯誤  
  
1.  決定哪個成員應該是類別、結構或介面的預設成員。  
  
2.  移除衝突的宣告 \(`Default` 關鍵字或 <xref:System.Reflection.DefaultMemberAttribute>\)。  
  
## 請參閱  
 <xref:System.Reflection.DefaultMemberAttribute>   
 [Default](../Topic/Default%20\(Visual%20Basic\).md)   
 [不在組建中：預設屬性](http://msdn.microsoft.com/zh-tw/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)