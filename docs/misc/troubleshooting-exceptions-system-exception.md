---
title: "疑難排解例外狀況：System.Exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Exception 例外狀況"
  - "基底類別, 例外狀況"
  - "例外狀況, 基底類別"
ms.assetid: fc15931a-9323-47c6-a42f-55d0534b939a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Exception
代表應用程式執行期間所發生的錯誤。 這是所有例外狀況的基底類別。  
  
## 相關秘訣  
 **如需詳細資訊，請查閱 InnerException 屬性。**  
 若要修正錯誤，您可能需要導致目前例外狀況之內部 \(或先前\) 例外的相關資訊。 目前例外狀況的 <xref:System.Exception.InnerException%2A> 屬性中包含內部例外。 您可以使用 \[**例外狀況助理**\] 對話方塊中的 \[**檢視詳細資料**\] 連結來存取 <xref:System.Exception.InnerException%2A> 屬性。  
  
 **\[暫時關閉 Just My Code 偵錯。\]**  
 例外狀況可能發生在不是您所寫的程式碼中。 若要偵錯該程式碼，您可能必須關閉 Just My Code 偵錯。 如需詳細資訊，請參閱[選項對話方塊、偵錯、一般](../Topic/General,%20Debugging,%20Options%20Dialog%20Box.md)。  
  
## 請參閱  
 <xref:System.Exception>   
 <xref:System.Exception.InnerException%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：當擲回例外狀況時中斷](../misc/how-to-break-when-an-exception-is-thrown.md)   
 [選項對話方塊、偵錯、一般](../Topic/General,%20Debugging,%20Options%20Dialog%20Box.md)