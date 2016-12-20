---
title: "這個由編譯器所發現的 &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; 自訂版本無效 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36558"
  - "bc36558"
helpviewer_keywords: 
  - "BC36558"
ms.assetid: f47d310a-95fd-4340-bda2-21262c217dbb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 這個由編譯器所發現的 &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; 自訂版本無效
這個由編譯器所發現的 'System.Runtime.CompilerServices.ExtensionAttribute' 自訂版本無效。 它的屬性使用方式旗標必須設定成允許組件、類別和方法。  
  
 這個由編譯器所發現的 <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> 自訂版本，未將其屬性使用方式旗標設定成允許將屬性套用至組件、方法和類別。 您必須至少套用至上述三個程式項目。  
  
 **錯誤 ID︰**BC36558  
  
### 更正這個錯誤  
  
-   變更屬性定義，以允許將屬性至少套用至組件、方法和類別，如下列範例所示。  
  
-   使用 <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName>，而不是自訂版本。  
  
## 範例  
 下列範例使用 `AttributeUsage` 屬性指定新版 `ExtensionAttribute` 可以套用至哪些程式項目。 此範例指定 `AttributeTargets` 列舉的三個成員：`Assembly`、`Class` 和 `Method`。 省略其中任何一個項目都會造成這個錯誤。  
  
```  
Namespace System.Runtime.CompilerServices <AttributeUsage(AttributeTargets.Assembly Or _ AttributeTargets.Class Or AttributeTargets.Method)> Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
 或者，您可以使用 `AttributeTargets` 的 `All` 成員，允許 `ExtensionAttribute` 套用至所有程式項目。  
  
```  
<AttributeUsage(AttributeTargets.All)>  
```  
  
 刪除 `AttributeUsage` 行 \(如下列程式碼所示\) 會產生相同的結果。  
  
```  
Namespace System.Runtime.CompilerServices Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [不在組建中：Visual Basic 屬性概觀](http://msdn.microsoft.com/zh-tw/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [不在組建中：Visual Basic 中的自訂屬性](http://msdn.microsoft.com/zh-tw/d72d8a5c-8f64-4614-b15b-cad66845d047)   
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [不在組建中：如何：定義您自己的屬性](http://msdn.microsoft.com/zh-tw/039609c4-ec43-4f44-945f-aa3b5b535c6a)   
 [撰寫自訂屬性](../Topic/Writing%20Custom%20Attributes.md)