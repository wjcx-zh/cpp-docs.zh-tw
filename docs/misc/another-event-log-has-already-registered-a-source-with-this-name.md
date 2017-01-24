---
title: "另一個事件記錄檔已經註冊此名稱的來源 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 另一個事件記錄檔已經註冊此名稱的來源
嘗試將項目寫入事件記錄檔，其中指定的來源已向另一個事件記錄檔登錄。  
  
 您必須設定您 <xref:System.Diagnostics.EventLog> 元件執行個體的 <xref:System.Diagnostics.EventLog.Source%2A> 屬性，元件才能將項目寫入記錄檔。 當發生這種情況時，系統會檢查您所指定的來源已向元件寫入的事件記錄檔登錄，並視需要呼叫 <xref:System.Diagnostics.EventLog.CreateEventSource%2A>。  
  
### 更正這個錯誤  
  
1.  請使用 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 或 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 方法移除來源與第一個記錄檔的關聯。  
  
2.  向新的記錄檔登錄來源。  
  
## 請參閱  
 [My.Application.Log 物件](../Topic/My.Application.Log%20Object.md)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/zh-tw/bc66c900-4b8a-426a-b8e2-17031a20167e)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/zh-tw/948ff920-a739-4e66-a191-ee951512d42c)