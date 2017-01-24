---
title: "疑難排解例外狀況：System.MissingMemberException | Microsoft Docs"
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
  - "MissingMemberException 類別"
ms.assetid: c4cf497b-0554-47fe-b2e9-81ee3eb9ec04
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.MissingMemberException
嘗試動態存取不存在的類別成員時，就會擲回 <xref:System.MissingMemberException> 例外狀況。  
  
## 相關秘訣  
 **如果移除或重新命名類別庫 \(Class Library\) 中的成員，請重新編譯參考該類別庫的任何組件。**  
 在某一組件中刪除或重新命名欄位或方法，但這項變更未反映在嘗試存取遺漏成員的第二個組件時，通常就會擲回這個例外狀況。  
  
 **如果您要存取晚期繫結物件變數上的成員，請確定它是宣告為 Public。**  
 在 Visual Basic 中，`Protected`、`Friend` 和 `Private` 變數不能是晚期繫結。  
  
## 請參閱  
 <xref:System.MissingMemberException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)