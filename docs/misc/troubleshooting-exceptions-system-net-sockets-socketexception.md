---
title: "疑難排解例外狀況：System.Net.Sockets.SocketException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "SocketException 類別"
ms.assetid: 89e8194d-83b0-450f-91f5-548e5c13944d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Net.Sockets.SocketException
當網路發生錯誤時，<xref:System.Net.Sockets.SocketException> 和 <xref:System.Net.Sockets.Socket> 類別就會擲回 <xref:System.Net.Dns> 例外狀況。  
  
## 相關秘訣  
 **請檢查 Errorcode 屬性，判斷通訊端 \(Socket\) 錯誤發生的原因。**  
 <xref:System.Net.Sockets.SocketException> 類別的預設建構函式，會將 <xref:System.Net.Sockets.SocketException.ErrorCode%2A> 屬性設定為最後發生的作業系統通訊端錯誤。  
  
## 請參閱  
 <xref:System.Net.Sockets.SocketException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [使用安全通訊端層](../Topic/Using%20Secure%20Sockets%20Layer.md)