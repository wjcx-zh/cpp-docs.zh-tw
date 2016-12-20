---
title: "疑難排解例外狀況：System.IO.PathTooLongException | Microsoft Docs"
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
  - "PathTooLongException 類別"
ms.assetid: 8912c425-bf91-42e3-82d8-bee6b2062db3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IO.PathTooLongException
當路徑名稱或檔案名稱超過系統定義的最大長度時，就會擲回 <xref:System.IO.PathTooLongException> 例外狀況。  
  
## 相關秘訣  
 **請確定路徑未超過系統定義的最大長度。**  
 在 Windows 架構的平台上，路徑必須少於 248 個字元，檔案名稱必須少於 260 個字元。  
  
## 請參閱  
 <xref:System.IO.PathTooLongException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：剖析檔案路徑](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)