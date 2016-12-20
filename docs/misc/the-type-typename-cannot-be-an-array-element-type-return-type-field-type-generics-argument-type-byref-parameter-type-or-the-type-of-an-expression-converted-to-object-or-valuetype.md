---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 不能是陣列項目類型、傳回類型、欄位類型、泛型引數類型、&#39;ByRef&#39; 參數類型或轉換成 &#39;Object&#39; 或 &#39;ValueType&#39; 的運算式類型 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31396"
  - "BC31396"
helpviewer_keywords: 
  - "BC31396"
ms.assetid: 56998a2c-a705-482e-87ee-5eff707f8a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 不能是陣列項目類型、傳回類型、欄位類型、泛型引數類型、&#39;ByRef&#39; 參數類型或轉換成 &#39;Object&#39; 或 &#39;ValueType&#39; 的運算式類型
運算式宣告變數、程序參數、類型參數、函式傳回或陣列是屬於受限制的類型。  
  
 Common Language Runtime \(CLR\) 會僅針對特語言支援而公開特定類型，且它們不應該用來作為您應用程式中的資料類型。 這些類型包括 <xref:System.ArgIterator>、<xref:System.RuntimeArgumentHandle> 和 <xref:System.TypedReference> 結構。  
  
 **錯誤 ID︰**BC31396  
  
### 更正這個錯誤  
  
-   請勿使用受限制的結構作為宣告的資料類型。  
  
## 請參閱  
 <xref:System.ArgIterator>   
 <xref:System.RuntimeArgumentHandle>   
 <xref:System.TypedReference>