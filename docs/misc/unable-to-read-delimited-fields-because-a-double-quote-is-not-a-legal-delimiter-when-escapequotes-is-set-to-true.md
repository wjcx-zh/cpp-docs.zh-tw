---
title: "當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。 | Microsoft Docs"
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
  - "vbrTextFieldParser_IllegalDelimiter"
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。
`TextFieldParser` 無法從檔案讀取，因為引號 \("\) 已供做分隔符號且 `EscapeQuotes` 設為 `True`。  
  
### 更正這個錯誤  
  
-   請設定 `EscapeQuotes` 為 `False`。  
  
## 請參閱  
 [TextFieldParser.SetDelimiters 方法](http://msdn.microsoft.com/zh-tw/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [TextFieldParser.Delimiters 屬性](http://msdn.microsoft.com/zh-tw/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](../Topic/TextFieldParser%20Object.md)