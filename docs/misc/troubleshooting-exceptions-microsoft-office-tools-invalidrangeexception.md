---
title: "疑難排解例外狀況：Microsoft.Office.Tools.InvalidRangeException | Microsoft Docs"
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
  - "Microsoft.Office.Tools.InvalidRangeException 例外狀況"
ms.assetid: 0deea25b-1152-40b6-89e2-e2e9c85f7dc0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：Microsoft.Office.Tools.InvalidRangeException
當您以程式設計的方式，建立展開多個區域範圍的檢視控制項時，則會擲回 <xref:Microsoft.Office.Tools.InvalidRangeException> 例外狀況。  
  
## 相關秘訣  
 請確認範圍涵蓋的區域並未與其他範圍重疊。  
 範圍不能重疊。  
  
 請確認以程式設計方式所建立的檢視控制項，只有包含單一區域。  
 -   請確認以程式設計方式所建立的檢視控制項，只有包含單一區域，換句話說，在此區域中的所有儲存格。  
  
## 請參閱  
 <xref:Microsoft.Office.Tools.InvalidRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)