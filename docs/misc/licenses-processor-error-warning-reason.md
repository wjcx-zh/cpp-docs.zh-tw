---
title: "Licenses processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_task"
ms.assetid: 85750198-7bd3-4936-b1eb-954dcc3ff573
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Licenses processor error/warning: &lt;reason&gt;
如果工具在處理 .licx 檔案時傳回錯誤或警告，就會顯示錯誤或警告訊息。  專案系統會將 Licenses.licx 檔 \(如果有的話\) 轉換為 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 授權管理員可解讀的二進位檔案 \(Binary File\)，當做建置處理序的一部分。  這項轉換會使用同處理序 \(In\-Process\) 工具來完成。  
  
 此類錯誤或警告最可能的原因就是 .licx 檔毀壞。  如果 .licx 檔已在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 外部進行編輯或在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 內使用文字編輯器進行編輯過，則檔案可能會損毀。  
  
 這些檔案一般是由 Windows Form 和 Web Form 設計工具所管理。  
  
### 若要更正這個錯誤  
  
1.  修正 .licx 檔案的格式。  
  
     錯誤表示二進位檔案尚未產生，建置處理序將會失敗。  警告僅做為訊息目的。  
  
## 請參閱  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/zh-tw/f793852c-da06-4d52-a826-65f635844772)