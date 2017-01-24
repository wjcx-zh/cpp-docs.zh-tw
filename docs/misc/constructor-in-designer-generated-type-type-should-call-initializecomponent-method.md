---
title: "設計工具產生的類型 &#39;&lt;類型&gt;&#39; 中的 &#39;&lt;建構函式&gt;&#39;，應該呼叫 InitializeComponent 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40054"
  - "bc40054"
helpviewer_keywords: 
  - "BC40054"
ms.assetid: beac93b0-d427-4df6-9582-fd69c7a53673
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 設計工具產生的類型 &#39;&lt;類型&gt;&#39; 中的 &#39;&lt;建構函式&gt;&#39;，應該呼叫 InitializeComponent 方法
設計工具產生之類型中的建構函式未呼叫類型的 `InitializeComponent` 方法。  
  
 設計工具產生之類型中的每個建構函式都應該呼叫類型的 `InitializeComponent` 方法。  
  
 **錯誤 ID︰**BC40054  
  
### 更正這個錯誤  
  
-   請在建構函式中加入 `InitializeComponent` 方法的呼叫。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute>   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)