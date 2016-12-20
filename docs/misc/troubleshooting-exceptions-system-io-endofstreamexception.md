---
title: "疑難排解例外狀況：System.IO.EndOfStreamException | Microsoft Docs"
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
  - "EndOfStreamException 類別"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IO.EndOfStreamException
嘗試讀取的範圍超過資料流的結尾時，就會擲回 <xref:System.IO.EndOfStreamException> 例外狀況。  
  
## 相關秘訣  
 **進行讀取動作前，請先檢查是否已到檔案結尾。**  
 從資料流讀取之前，先使用 <xref:System.IO.StreamReader.Peek%2A> 方法檢查該檔案的結尾。  
  
## 請參閱  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：讀取和寫入新建立的資料檔案](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [如何：開啟並附加至記錄檔](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)