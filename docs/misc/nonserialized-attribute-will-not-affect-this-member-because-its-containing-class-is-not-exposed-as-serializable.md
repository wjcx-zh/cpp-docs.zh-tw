---
title: "&#39;NonSerialized&#39; 屬性對這個成員將沒有任何作用，因為它的包含類別並未公開為 &#39;Serializable&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30772"
  - "bc30772"
helpviewer_keywords: 
  - "BC30772"
ms.assetid: 1014e944-40c1-4078-8a38-139736ef89da
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;NonSerialized&#39; 屬性對這個成員將沒有任何作用，因為它的包含類別並未公開為 &#39;Serializable&#39;
根據預設，類別和其成員都是不可序列化的。 只有在不應該序列化可序列化類別的成員時，才需要 <xref:System.NonSerializedAttribute> 屬性。  
  
 **錯誤 ID︰**BC30772  
  
### 更正這個錯誤  
  
-   將 <xref:System.SerializableAttribute> 屬性加入該類別。  
  
     \-或\-  
  
-   從成員中移除 <xref:System.NonSerializedAttribute> 屬性。  
  
## 請參閱  
 <xref:System.NonSerializedAttribute>   
 <xref:System.SerializableAttribute>   
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)