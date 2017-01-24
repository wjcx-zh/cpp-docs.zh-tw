---
title: "XML 常值不可出現在這裡，除非加上括弧 | Microsoft Docs"
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
  - "bc31198"
  - "vbc31198"
helpviewer_keywords: 
  - "BC31198"
ms.assetid: 97b16076-39ff-430a-9c65-073d01bcb08e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML 常值不可出現在這裡，除非加上括弧
運算式中使用的 XML 常值宣告，其位置對 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器來說模稜兩可。 也就是說，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器無法判斷小於字元 \(\<\) 要當做比較運算子還是 XML 常值的開頭。 下列程式碼提供一個範例：  
  
 \[Visual Basic\]  
  
```  
' Generates an error. Dim queryResult = From element In elements _ Where <sample>Value</sample> = "Value" _ Select element  
```  
  
 **錯誤 ID：**BC31198  
  
### 更正這個錯誤  
  
-   將 XML 常值宣告用括弧括住，如下列範例所示：  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where (<sample> Value</sample>) = "Value" _ Select element  
    ```  
  
-   修改程式碼以參考現有的 XML 常值，如下列範例所示：  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where e.<sample>.Value = "Value" _ Select element  
    ```  
  
## 請參閱  
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML Axis Properties](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)