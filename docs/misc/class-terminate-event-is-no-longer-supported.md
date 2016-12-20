---
title: "不再支援 &#39;Class_Terminate&#39; 事件 | Microsoft Docs"
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
  - "vbc42002"
  - "bc42002"
helpviewer_keywords: 
  - "BC42002"
ms.assetid: 11eeac74-666d-4b23-81bc-b1691290ddd0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不再支援 &#39;Class_Terminate&#39; 事件
不再支援 'Class\_Terminate' 事件。 請使用 'Sub Finalize' 來釋放資源。  
  
 舊版 Visual Basic 的 `Class_Terminate` 事件已取代為類別解構函式。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42002  
  
### 更正這個錯誤  
  
-   宣告名為 `Finalize` 的 `Sub` 程序來終止類別。 記憶體回收行程偵測到沒有其他使用中執行個體參考時，呼叫 `Sub Finalize`。  
  
## 請參閱  
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/zh-tw/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [不在組建中：如何：實作 Dispose Finalize 模式 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/adf7a232-4ebb-485d-8626-8d64421eb0c4)