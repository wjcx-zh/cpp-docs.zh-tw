---
title: "&#39;prefix&#39; 是 XML 前置詞，無法當成運算式使用。 | Microsoft Docs"
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
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;prefix&#39; 是 XML 前置詞，無法當成運算式使用。
'prefix' 是 XML 前置詞，無法當成運算式使用。 使用 GetXmlNamespace 運算子建立命名空間物件。  
  
 使用 `Imports` 陳述式匯入的 XML 命名空間前置詞無法在 XML 常值外使用。  
  
 **錯誤識別碼：**BC30114  
  
### 更正這個錯誤  
  
-   如果必須參考匯入的 XML 命名空間的一部分，請使用 `GetXmlNamespace` 運算子來擷取 <xref:System.Xml.Linq.XNamespace> 物件。 使用該物件，不使用 XML 命名空間前置詞。  
  
-   如果要使用 XML 命名空間前置詞限定 XML 常值，請確定 XML 常值使用正確的語法。  
  
## 請參閱  
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [Imports Statement \(XML Namespace\)](../Topic/Imports%20Statement%20\(XML%20Namespace\).md)   
 [GetXmlNamespace Operator](../Topic/GetXmlNamespace%20Operator%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)