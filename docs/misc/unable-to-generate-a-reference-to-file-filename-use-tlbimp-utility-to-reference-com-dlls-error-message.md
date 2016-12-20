---
title: "無法產生對檔案 &#39;&lt;檔案名稱&gt;&#39; 的參考 (使用 TLBIMP 公用程式參考 COM DLL)：&lt;錯誤訊息&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30142"
  - "bc30142"
helpviewer_keywords: 
  - "BC30142"
ms.assetid: ee0f2c77-3714-4ec2-bddf-d098ab77722f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法產生對檔案 &#39;&lt;檔案名稱&gt;&#39; 的參考 (使用 TLBIMP 公用程式參考 COM DLL)：&lt;錯誤訊息&gt;
[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器呼叫組件連結器 \(Al.exe，也稱為 Alink\) 使用資訊清單產生組件。 連結器報告在尋找或驗證 COM \+ DLL 檔案時發生錯誤。  
  
 **錯誤 ID︰**BC30142  
  
### 更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並參考 [Al.exe 工具錯誤和警告](http://msdn.microsoft.com/zh-tw/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)的主題，以取得進一步說明和建議。  
  
2.  如果想要的參考是針對 COM DLL，而不是 COM \+ DLL，請使用 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) 來產生參考。  
  
3.  如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## 請參閱  
 [Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe 工具錯誤和警告](http://msdn.microsoft.com/zh-tw/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [PAVEOVER 產品支援和協助工具](http://msdn.microsoft.com/zh-tw/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)