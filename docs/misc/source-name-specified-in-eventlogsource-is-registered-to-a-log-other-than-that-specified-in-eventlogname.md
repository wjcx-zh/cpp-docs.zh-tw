---
title: "在 EventLogSource 中指定的來源名稱會登錄到不在 EventLogName 指定的記錄檔 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 EventLogSource 中指定的來源名稱會登錄到不在 EventLogName 指定的記錄檔
`EventLog` 嘗試參考登錄到不同記錄檔的來源。 如果要將項目寫入事件記錄檔，您必須指定 <xref:System.Diagnostics.EventLog.Source%2A> 屬性。<xref:System.Diagnostics.EventLog.Source%2A> 屬性會將元件和事件記錄登錄為有效的項目來源。 單一來源一次只能和一筆事件記錄建立關聯 \(因此寫入項目\)。  
  
 根據預設，如果您嘗試寫入項目，卻沒有先將元件登錄為有效的來源，系統會使用 <xref:System.Diagnostics.EventLog.Source%2A> 屬性的值當做來源字串，自動登錄來源和事件記錄。  
  
### 更正這個錯誤  
  
-   請確定來源已登錄到正確的記錄檔。 若要這樣做，請使用 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 方法或其多載之一，指定可向事件記錄檔唯一識別元件的字串。  
  
## 請參閱  
 [Administering Event Logs](http://msdn.microsoft.com/zh-tw/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [Event Log References](http://msdn.microsoft.com/zh-tw/4af0661c-6c96-49f4-961d-b26ed9bc3e87)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/zh-tw/948ff920-a739-4e66-a191-ee951512d42c)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/zh-tw/bc66c900-4b8a-426a-b8e2-17031a20167e)