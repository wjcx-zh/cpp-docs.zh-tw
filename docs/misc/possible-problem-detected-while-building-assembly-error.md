---
title: "建置組件時偵測到的可能問題：&lt;錯誤&gt; | Microsoft Docs"
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
  - "vbc40009"
  - "bc40009"
helpviewer_keywords: 
  - "BC40009"
ms.assetid: 4bc5108a-a96e-43be-8bba-a47441a25f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 建置組件時偵測到的可能問題：&lt;錯誤&gt;
由 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器呼叫的 ALink 工具回報建置組件時發生錯誤。 一個可能的原因是已簽署的組件參考未簽署的組件。  
  
 這個訊息是一個警告。 編譯器會繼續產生組件。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40009  
  
### 更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  再次編譯程式，看看錯誤是否重複發生。  
  
3.  如果問題重複發生，請重新安裝 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器。  
  
4.  如果重新安裝之後，錯誤仍持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## 請參閱  
 [PAVEOVER 產品支援和協助工具](http://msdn.microsoft.com/zh-tw/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)