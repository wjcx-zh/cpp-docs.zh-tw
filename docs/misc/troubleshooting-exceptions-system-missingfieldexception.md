---
title: "疑難排解例外狀況：System.MissingFieldException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "MissingFieldException 類別"
ms.assetid: afa4d669-7d08-4b14-8341-36717a5054d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.MissingFieldException
嘗試動態存取不存在的欄位時，就會擲回 <xref:System.MissingFieldException> 例外狀況。  
  
## 相關秘訣  
 **如果類別庫 \(Class Library\) 中的欄位被移除或重新命名，請重新編譯參考該類別庫的任何組件。**  
 嘗試動態存取已刪除或重新命名的組件欄位，而該組件未以其強式名稱 \(Strong Name\) 參照時，就會產生這個例外狀況。  
  
## 請參閱  
 <xref:System.MissingFieldException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)