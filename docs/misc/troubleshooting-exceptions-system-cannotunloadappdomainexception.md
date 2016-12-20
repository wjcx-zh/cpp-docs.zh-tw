---
title: "疑難排解例外狀況：System.CannotUnloadAppDomainException | Microsoft Docs"
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
  - "CannotUnloadAppDomainException 類別"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.CannotUnloadAppDomainException
嘗試卸載下列其中之一時，就會擲回 <xref:System.CannotUnloadAppDomainException> 例外狀況：  
  
-   預設的應用程式定義域，在應用程式的存留期 \(Lifetime\) 期間必須持續載入該定義域  
  
-   應用程式定義域，其中含有無法立刻停止執行的執行中執行緒  
  
-   已卸載的應用程式定義域  
  
## 相關秘訣  
 **請確定您未嘗試卸載預設、含有執行中執行緒，或已被卸載的應用程式。**  
 上述任何情況都會擲回這個例外狀況。 如需詳細資訊，請參閱<xref:System.AppDomain.Unload%2A>。  
  
## 請參閱  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)