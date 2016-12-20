---
title: "由於內部錯誤，無法取得完整作業系統名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrDiagnosticInfo_FullOSName"
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 由於內部錯誤，無法取得完整作業系統名稱
由於內部錯誤，無法取得完整作業系統名稱。 這可能是因為目前電腦上沒有 WMI 存在所造成。  
  
 呼叫 `My.Computer.Info.OSFullName` 屬性失敗。 如果目前電腦上未安裝 Windows Management Instrumentation \(WMI\)，就可能會發生這項失敗。  
  
### 更正這個錯誤  
  
1.  將包圍呼叫的 `Try...Catch` 區塊加入 `My.Computer.Info.OSFullName` 屬性中。  
  
2.  如需 WMI 及其安裝方式的詳細資訊，請前往  並搜尋 "Windows Management Instrumentation Core"。  
  
## 請參閱  
 [My.Computer.Info.OSFullName 屬性](http://msdn.microsoft.com/zh-tw/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)