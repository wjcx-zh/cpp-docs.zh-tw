---
title: "疑難排解例外狀況：System.NotCancelableException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NotCancelableException 類別"
ms.assetid: 36b82d4b-f075-4af5-993a-3e763a7e254a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.NotCancelableException
嘗試取消無法取消的作業時，就會擲回 `NotCancelableException`。  
  
## 相關秘訣  
 不要嘗試取消作業。  
 進行這類的嘗試時，某些作業會因為無法取消而擲回這個例外狀況。 在這種情況中，請避免提供使用者取消作業的選項。  
  
## 請參閱  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)