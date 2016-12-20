---
title: "建置組件 &#39;&lt;組件名稱&gt;&#39; 時偵測到的可能問題：&lt;錯誤&gt; | Microsoft Docs"
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
  - "vbc40010"
  - "bc40010"
helpviewer_keywords: 
  - "BC40010"
ms.assetid: 3a4f4a4a-a5ad-4501-bf4c-0fbf25c50734
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 建置組件 &#39;&lt;組件名稱&gt;&#39; 時偵測到的可能問題：&lt;錯誤&gt;
由 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器呼叫的 ALink 工具回報建置組件時發生錯誤。 可能的原因包括：  
  
-   已簽署的組件參考未簽署的組件。 在此情況下，您應該考慮參考的組件是否符合安全性準則。  
  
-   在 32 位元平台上建置 64 位元應用程式。 在此情況下，您必須確定目標平台上已安裝 64 位元版本的所有參考組件。 對於 Common Language Runtime \(CLR\) 組件，這會自動進行處理，但是仍會產生這則錯誤訊息。  
  
 這個訊息是一個警告。 編譯器會繼續產生組件。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40010  
  
### 更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  再次編譯程式，看看錯誤是否重複發生。  
  
3.  如果問題重複發生，請重新安裝 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器。  
  
4.  如果重新安裝之後，錯誤仍持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## 請參閱  
 [PAVEOVER 產品支援和協助工具](http://msdn.microsoft.com/zh-tw/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)   
 [Common Language Runtime Overview](http://msdn.microsoft.com/zh-tw/0fd9aeae-af10-435f-86d4-e76619741e4a)