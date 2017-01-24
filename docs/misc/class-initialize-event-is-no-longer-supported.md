---
title: "不再支援 &#39;Class_Initialize&#39; 事件 | Microsoft Docs"
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
  - "vbc42001"
  - "bc42001"
helpviewer_keywords: 
  - "BC42001"
ms.assetid: 31e7c383-894e-416c-b834-3688cc340ccf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不再支援 &#39;Class_Initialize&#39; 事件
不再支援 'Class\_Initialize' 事件。 請使用 'Sub New' 初始化類別。  
  
 類別建構函式已取代舊版 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 的 `Class_Initialize` 事件。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID：**BC42001  
  
### 更正這個錯誤  
  
-   宣告一或多個名為 `New` 的 `Sub` 程序來初始化類別。 新建類別執行個體時會呼叫 `Sub New`。  
  
## 請參閱  
 [Class\_Initialize Changes in Visual Basic](http://msdn.microsoft.com/zh-tw/2cd023cf-2869-4836-b08d-43822294beeb)   
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/zh-tw/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)