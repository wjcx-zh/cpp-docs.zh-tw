---
title: "Resources processor error/warning: &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_task"
ms.assetid: eb9a1bd0-7e63-4a2b-ad37-54f6e67d9b5a
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources processor error/warning: &lt;reason&gt;
如果工具在處理 .resx 檔時傳回錯誤或警告，就會顯示錯誤或警告訊息。  專案系統會將每個 .resx 檔轉換為 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 資源管理員可解讀的二進位檔案，當做建置處理序的一部分。  這項轉換會使用同處理序 \(In\-Process\) 工具來完成。  
  
 此類錯誤或警告最可能的原因就是 .resx 檔毀壞。  如果 .resx 檔已在 Visual Studio 外編輯或在 Visual Studio 內使用文字編輯器編輯過，則檔案可能會損毀。  
  
 這些檔案一般是由 Windows Form 和 Web Form 設計工具所管理。  
  
### 若要更正這個錯誤  
  
1.  修正 .resx 檔案的格式。  
  
     錯誤表示二進位檔案尚未產生，建置處理序將會失敗。  警告僅做為訊息目的。  
  
## 請參閱  
 [Resources in .Resx File Format](http://msdn.microsoft.com/zh-tw/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)