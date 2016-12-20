---
title: "TextFieldParser 不支援包含空白字元的註解語彙基元 | Microsoft Docs"
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
  - "vbrTextFieldParser_WhitespaceInToken"
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# TextFieldParser 不支援包含空白字元的註解語彙基元
已提供包含空白字元的註解語彙基元。`TextFieldParser` 不支援包含空白字元的註解語彙基元，除非空白字元發生在語彙基元的開頭。 發生在語彙基元開頭的空白字元會被忽略。  
  
### 更正這個錯誤  
  
-   請提供正確的註解語彙基元。  
  
## 請參閱  
 [TextFieldParser.CommentTokens 屬性](http://msdn.microsoft.com/zh-tw/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)   
 [Parsing Text Files with the TextFieldParser Object](../Topic/Parsing%20Text%20Files%20with%20the%20TextFieldParser%20Object%20\(Visual%20Basic\).md)   
 [TextFieldParser Object](../Topic/TextFieldParser%20Object.md)