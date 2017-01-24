---
title: "除了最後項目以外的所有欄位寬度都必須大於零 | Microsoft Docs"
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
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 除了最後項目以外的所有欄位寬度都必須大於零
除了最後項目以外的所有欄位寬度都必須大於零。 最後項目的欄位寬度小於或等於零，表示最後欄位是可變長度。  
  
 作業失敗，因為除了最後項目以外的欄位寬度都設定為等於或小於零。 小於或等於零的欄位寬度可以用作最後項目，表示最後欄位是可變長度，但不能用作任何其他項目。  
  
### 更正這個錯誤  
  
-   將欄位寬度設定為正確的長度。  
  
## 請參閱  
 [TextFieldParser.SetFieldWidths 方法](http://msdn.microsoft.com/zh-tw/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [TextFieldParser.FieldWidths 屬性](http://msdn.microsoft.com/zh-tw/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [How to: Read From Fixed\-width Text Files](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](../Topic/TextFieldParser%20Object.md)