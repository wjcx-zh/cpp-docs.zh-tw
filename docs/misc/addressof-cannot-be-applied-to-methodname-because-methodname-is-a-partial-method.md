---
title: "無法將 &#39;AddressOf&#39; 套用至 &#39;methodname&#39;，因為 &#39;methodname&#39; 是部分方法 | Microsoft Docs"
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
  - "vbc31440"
  - "bc31440"
helpviewer_keywords: 
  - "BC31440"
ms.assetid: 924dbada-3e0a-4004-a3ae-a209b7c3d1fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;AddressOf&#39; 套用至 &#39;methodname&#39;，因為 &#39;methodname&#39; 是部分方法
部分方法已傳遞至 `AddressOf` 運算子。 部分方法是 `AddressOf` 運算子的無效值。  
  
 **錯誤 ID︰**BC31440  
  
### 更正這個錯誤  
  
1.  加入部分方法的實作方法。 實作方法是 `AddressOf` 運算子的有效值。 下列範例會示範部分方法簽章及其實作。  
  
    ```vb#  
    ' Definition of the partial method signature.  
    Partial Private Sub OnNameChanged()  
        ' The body of the signature is empty.  
    End Sub  
  
    ' Implementation of the partial method.  
    Private Sub OnNameChanged()  
        MsgBox("Name was changed to " & Me.Name)  
    End Sub  
    ```  
  
## 請參閱  
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)