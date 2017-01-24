---
title: "內嵌運算式的開頭必須是 &#39;%=&#39; | Microsoft Docs"
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
  - "vbc31179"
  - "bc31179"
helpviewer_keywords: 
  - "BC31179"
ms.assetid: 20b0382e-1744-47e4-84e1-7fc926cbc4df
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 內嵌運算式的開頭必須是 &#39;%=&#39;
內嵌運算式的起始識別項 `<%=` 未正確編碼。 請注意，您無法在 XML 項目常值的名稱中使用百分比字元 \(%\)。  
  
 **錯誤 ID︰**BC31179  
  
### 更正這個錯誤  
  
-   確定內嵌運算式的起始識別項未編碼為 `<%=`。  
  
## 請參閱  
 [Embedded Expressions in XML](../Topic/Embedded%20Expressions%20in%20XML%20\(Visual%20Basic\).md)   
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)