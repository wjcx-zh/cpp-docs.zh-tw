---
title: "疑難排解例外狀況：System.TypeInitializationException | Microsoft Docs"
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
  - "TypeInitializationException 例外狀況"
  - "System.TypeInitializationException 例外狀況"
ms.assetid: c77e81fd-1518-49a1-8213-3f169658f5f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.TypeInitializationException
因為當做類別初始設定式 \(Class Initializer\) 所擲回例外狀況的包裝函式，所擲回的例外狀況。  
  
## 備註  
 當類別初始設定式無法初始化型別時，<xref:System.TypeInitializationException> 便會建立並傳遞參考至型別之類別初始設定式所擲回的例外狀況。<xref:System.Exception.InnerException%2A> 的 <xref:System.TypeInitializationException> 屬性會含有基礎例外狀況。  
  
## 請參閱  
 <xref:System.TypeInitializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)