---
title: "疑難排解例外狀況：System.FieldAccessException | Microsoft Docs"
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
  - "FieldAccessException 類別"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.FieldAccessException
嘗試存取類別內部私用或受保護欄位而無效時，就會擲回 <xref:System.FieldAccessException> 例外狀況。  
  
## 相關秘訣  
 **如果類別庫中某個欄位的存取層級變更了，請重新編譯參考該類別庫的所有組件。**  
 當類別庫中欄位的存取層級 \(`Public`、`Private` 等等\) 遭變更，而且未重新編譯參照該類別庫的一或多個組件時，通常會擲回這個例外狀況。  
  
## 請參閱  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)