---
title: "疑難排解例外狀況：System.ObjectDisposedException | Microsoft Docs"
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
  - "ObjectDisposedException 類別, 疑難排解"
ms.assetid: 702912b6-e927-4f8e-8b7c-2e1880312b0e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.ObjectDisposedException
嘗試在已處置的物件 \(例如關閉的資料流或登錄機碼\) 上作業時，就會擲回 <xref:System.ObjectDisposedException> 例外狀況。  
  
## 相關秘訣  
 **嘗試使用資源之前，先確定您尚未釋放該資源。**  
 例如，嘗試操作資料流時，請確定先前未關閉該資料流。  
  
## 請參閱  
 <xref:System.ObjectDisposedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)