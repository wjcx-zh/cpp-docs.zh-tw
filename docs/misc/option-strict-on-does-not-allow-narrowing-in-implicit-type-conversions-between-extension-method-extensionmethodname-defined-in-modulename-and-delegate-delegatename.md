---
title: "Option Strict 為 On 時，不允許縮減在 &#39;&lt;模組名稱&gt;&#39; 中定義之擴充方法 &#39;&lt;擴充方法名稱&gt;&#39; 與委派 &#39;&lt;委派名稱&gt;&#39; 之間的隱含類型轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36709"
  - "vbc36709"
helpviewer_keywords: 
  - "BC36709"
ms.assetid: 95d8c833-3525-411b-98e8-b7d3f61f75c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict 為 On 時，不允許縮減在 &#39;&lt;模組名稱&gt;&#39; 中定義之擴充方法 &#39;&lt;擴充方法名稱&gt;&#39; 與委派 &#39;&lt;委派名稱&gt;&#39; 之間的隱含類型轉換
當 `Option Strict` 為 On 時，您不能縮減從委派的參數類型到指派給該委派類型變數之擴充方法對應參數的轉換。 委派參數的資料類型必須擴展為擴充方法的資料類型。  
  
 **錯誤 ID：**BC36709  
  
### 更正這個錯誤  
  
-   變更委派中參數或擴充方法的資料類型，以確保存在擴展關聯性。  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)   
 [Delegates](../Topic/Delegates%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)