---
title: "疑難排解例外狀況：System.Net.HttpListenerException | Microsoft Docs"
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
  - "HttpListenerException 類別"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Net.HttpListenerException
處理超文字傳輸通訊協定 \(Hypertext Transfer Protocol\) 要求發生錯誤時，就會擲回 <xref:System.Net.HttpListenerException>。  
  
## 相關秘訣  
 請確認您未嘗試註冊已被註冊的 URI 前置詞。  
 如果該 URI 前置詞已被註冊，就會發生這個例外狀況。  
  
 請確認您的 HTTP 要求是有效的。  
 在 <xref:System.Net.HttpListener> 初始化期間，或在建立或傳送 HTTP 要求的回應時發生錯誤，<xref:System.Net.HttpListener> 類別及其相關類別就會擲回這個例外狀況。  
  
 如果您正在使用 `HttpListenerPrefixCollection.Add` 方法，請確認未曾加入 `uriPrefix`。  
 如果另一個 <xref:System.Net.HttpListener> 已加入前置詞 `uriPrefix`，就會擲回這個例外狀況。  
  
## 請參閱  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)