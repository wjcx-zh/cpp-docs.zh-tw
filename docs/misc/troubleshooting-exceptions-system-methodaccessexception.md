---
title: "疑難排解例外狀況：System.MethodAccessException | Microsoft Docs"
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
  - "MethodAccessException 類別"
ms.assetid: 1c276666-e451-489e-8b95-25d737787030
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.MethodAccessException
如果無效存取類別內的私用方法或受保護的方法，就會擲回 <xref:System.MethodAccessException> 例外狀況。  
  
## 相關秘訣  
 **如果類別庫 \(Class Library\) 中方法的存取層級已經變更，請重新編譯參照該類別庫的任何組件。**  
 當呼叫端沒有該成員的存取權限時，就會發生這個例外狀況。  
  
## 請參閱  
 <xref:System.MethodAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)