---
title: "無法將 &#39;type1&#39; 轉換成 &#39;type2&#39; | Microsoft Docs"
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
  - "bc31193"
  - "vbc31193"
helpviewer_keywords: 
  - "BC31193"
ms.assetid: f25a9f5b-7741-4cd6-b85a-b19037ed8e49
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;type1&#39; 轉換成 &#39;type2&#39;
無法將 'type1' 轉換成 'type2'。 您可以使用 'Value' 屬性來取得 'parentElement' 的第一個項目的字串值。  
  
 已嘗試將 XML 常值隱含轉換成特定類型。 您無法將 XML 常值隱含轉換成指定的類型。  
  
 **錯誤 ID︰**BC31193  
  
### 更正這個錯誤  
  
-   使用 XML 常值的 `Value` 屬性以 `String` 形式來參考其值。 使用 `CType` 函式、另一個類型轉換函式或 <xref:System.Convert> 類別，將值轉換為指定的類型。  
  
## 請參閱  
 <xref:System.Convert>   
 [Accessing XML in Visual Basic](../Topic/Accessing%20XML%20in%20Visual%20Basic.md)   
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)   
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)