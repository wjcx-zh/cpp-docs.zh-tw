---
title: "疑難排解例外狀況：Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException 例外狀況"
ms.assetid: d780b8cc-c3f1-45ed-8f8e-3f8728a4b770
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException
當 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> 無法使用指定的格式剖析資料列時，便會擲回 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 例外狀況。  
  
 例外狀況物件的 `Error Line` 屬性會包含造成錯誤的一行文字。  
  
## 相關秘訣  
 **檢查以確定 TextFieldType 和 Delimiter 參數已適當地定義**  
 `TextFieldType` \(分隔或固定寬度\) 必須符合檔案的格式。 如果 `TextFieldType` 為 `FixedWidth`，請檢查 `FieldWidths` 屬性是否已正確地設定。 如果 `TextFieldType` 為 `Delimited`，請檢查 `Delimiters` 屬性是否已正確地設定。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 [Parsing Text Files with the TextFieldParser Object](../Topic/Parsing%20Text%20Files%20with%20the%20TextFieldParser%20Object%20\(Visual%20Basic\).md)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [How to: Read From Fixed\-width Text Files](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)