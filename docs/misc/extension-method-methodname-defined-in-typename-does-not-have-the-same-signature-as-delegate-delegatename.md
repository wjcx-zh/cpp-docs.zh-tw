---
title: "在 &#39;&lt;類型名稱&gt;&#39; 中定義的擴充方法 &#39;&lt;方法名稱&gt;&#39; 與委派 &#39;&lt;委派名稱&gt;&#39; 沒有相同的簽章 | Microsoft Docs"
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
  - "bc36580"
  - "vbc36580"
helpviewer_keywords: 
  - "BC36580"
ms.assetid: dc6b6a63-02b0-43d8-b6a7-c1cd397c6ee3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;&lt;類型名稱&gt;&#39; 中定義的擴充方法 &#39;&lt;方法名稱&gt;&#39; 與委派 &#39;&lt;委派名稱&gt;&#39; 沒有相同的簽章
您嘗試使用之擴充方法和委派的簽章不符。`Delegate` 陳述式定義委派類別的參數類型和傳回類型。 任何具有相符參數、類型和傳回類型的程序都可用來建立這個委派類型的執行個體。 下列範例會報告這個錯誤，因為擴充方法的簽章 `Example` 與委派簽章 `Del` 不相容。  
  
```vb#  
' Definition of the delegate, with two parameters. Delegate Sub Del(ByVal m As Integer, ByVal s As String)  
```  
  
```vb#  
' Definition of the extension method, with one parameter. <Extension()> _ Sub Example(ByVal s As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
'' This assignment causes the error. ' Dim exampleDel As Del = AddressOf Example  
```  
  
 **錯誤 ID︰**BC36580  
  
### 更正這個錯誤  
  
-   確認委派和擴充方法的參數數目相同。  
  
-   確認委派和擴充方法中的參數順序相同。  
  
-   比較每個委派參數的資料類型與對應擴充方法參數的資料類型，以確定它們相容。  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)