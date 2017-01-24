---
title: "Option Strict 為 On 時，不可縮減方法 &#39;&lt;方法名稱&gt;&#39; 與委派 &#39;&lt;委派名稱&gt;&#39; 之間隱含的類型轉換 | Microsoft Docs"
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
  - "bc36663"
  - "vbc36663"
helpviewer_keywords: 
  - "BC36663"
ms.assetid: fefc7ab5-b587-4ff9-a6bc-4c4e5d4b6b29
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict 為 On 時，不可縮減方法 &#39;&lt;方法名稱&gt;&#39; 與委派 &#39;&lt;委派名稱&gt;&#39; 之間隱含的類型轉換
當 `Option Strict` 為 On 時，您不能在委派中的參數與函式的對應參數之間，或在與指派給該委派類型之變數的 `Sub` 之間，進行資料類型的縮小轉換。 例如，函式委派 `Del` 具有一個 `Integer` 類型的參數，而函式 `Conversion1`、`Conversion2` 和 `Conversion3` 具有一個不同數值類型的參數。  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String Function Conversion1(ByVal n As Integer) As String Return "Valid" End Function Function Conversion2(ByVal n As Long) As String Return "Valid" End Function Function Conversion3(ByVal n As Short) As String Return "Not valid" End Function  
```  
  
 由於從 `Integer` 到 `Integer` 及到 `Long` 有擴展轉換，因此下列指派有效。  
  
```vb#  
' Valid. Dim funDel1 As Del = AddressOf Conversion1 Dim funDel2 As Del = AddressOf Conversion2  
```  
  
 從 `Integer` 到 `Short` 的轉換是縮小轉換。 因此，下列指派無效。  
  
```vb#  
' Not valid. Dim funDel3 As Del = AddressOf Conversion3  
```  
  
 錯誤 ID︰BC36663  
  
### 更正這個錯誤  
  
-   變更委派中參數或方法的資料類型，以確保存在擴展關聯性。  
  
## 請參閱  
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)   
 [Delegates](../Topic/Delegates%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)