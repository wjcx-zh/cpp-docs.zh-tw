---
title: "方法 &#39;&lt;方法名稱&gt;&#39; 沒有與委派 &lt;&#39;委派名稱&#39;&gt; 相容的簽章 | Microsoft Docs"
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
  - "vbc31143"
  - "bc31143"
helpviewer_keywords: 
  - "BC31143"
ms.assetid: 88990637-7c92-467e-a3d3-db5498dc1dce
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 &#39;&lt;方法名稱&gt;&#39; 沒有與委派 &lt;&#39;委派名稱&#39;&gt; 相容的簽章
當方法與委派之間無法進行必要的轉換時，就會發生這個錯誤。 錯誤的原因可能在於參數之間的轉換，或在於傳回值中的轉換 \(當方法和委派為函式時\)。  
  
 下列程式碼描述失敗的轉換。 委派為 `FunDel`。  
  
```vb#  
Delegate Function FunDel(ByVal i As Integer, ByVal d As Double) As Integer  
```  
  
 下列各個函式與 `FunDel` 不同，而且其差異會造成這個錯誤。  
  
```vb#  
Function ExampleMethod1(ByVal m As Integer, ByVal aDate As Date) As Integer End Function Function ExampleMethod2(ByVal m As Integer, ByVal aDouble As Double) As Date End Function  
```  
  
 下列每個指派陳述式都會造成此錯誤。  
  
```vb#  
Sub Main() ' The second parameters of FunDel and ExampleMethod1, Double and Date, ' are not compatible. 'Dim d1 As FunDel = AddressOf ExampleMethod1 ' The return types of FunDel and ExampleMethod2, Integer and Date, ' are not compatible. 'Dim d2 As FunDel = AddressOf ExampleMethod2 End Sub  
```  
  
 **錯誤 ID︰**BC31143  
  
### 更正這個錯誤  
  
-   檢查對應的參數；如果存在這些參數，則傳回類型，以判斷哪一對不相容。  
  
## 請參閱  
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)   
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)