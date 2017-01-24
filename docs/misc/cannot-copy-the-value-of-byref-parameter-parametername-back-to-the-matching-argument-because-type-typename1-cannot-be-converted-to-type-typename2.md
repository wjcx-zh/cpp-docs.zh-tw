---
title: "無法將 &#39;ByRef&#39; 參數的值 &#39;&lt;參數名稱&gt;&#39; 複製回相對應的引數，因為類型 &#39;&lt;類型名稱1&gt;&#39; 無法轉換成類型 &#39;&lt;類型名稱2&gt;&#39; | Microsoft Docs"
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
  - "vbc33037"
  - "BC33037"
helpviewer_keywords: 
  - "BC33037"
ms.assetid: 3ff137e2-e062-4e54-abf5-e902e2d18968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;ByRef&#39; 參數的值 &#39;&lt;參數名稱&gt;&#39; 複製回相對應的引數，因為類型 &#39;&lt;類型名稱1&gt;&#39; 無法轉換成類型 &#39;&lt;類型名稱2&gt;&#39;
程序是宣告成具有無法轉換回呼叫中引數類型的參數類型。  
  
 當您定義類別或結構時，可以定義一個或多個轉換運算子，以將該類別或結構類型轉換成其他類型。 您也可以定義反向轉換運算子，以這些其他類型轉換回您的類別或結構類型。 當您在程序呼叫中使用類別或結構類型時，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 可以使用這些轉換運算子將引數的類型轉換成其對應參數的類型。  
  
 如果您傳遞 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md) 引數，則 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 有時會將引數值複製至程序中的區域變數，而不是傳遞參考。 在這類情況下，此程序傳回時，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 接著必須將區域變數值複製回呼叫中程式碼中的引數。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但是，如果類型不同，則 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 必須進行雙向轉換。 如果其中一種類型是類別或結構類型，則 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 必須將它轉換成其他類型，以及從其他類型轉換它。 這表示您必須定義雙向轉換運算子。  
  
 **錯誤 ID︰**BC33037  
  
### 更正這個錯誤  
  
-   如果可能，請使用類型與程序參數相同的呼叫中引數，這樣 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 就不需要執行任何轉換。  
  
-   如果您需要呼叫引數類型與參數類型不同的程序，但不需要將值傳回給呼叫中引數，請將此參數定義為 [ByVal](../Topic/ByVal%20\(Visual%20Basic\).md)，而非 `ByRef`。  
  
-   如果您需要將值傳回給呼叫中引數，請定義反向轉換運算子，這樣 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 就可以轉換回呼叫中引數類型。  
  
## 請參閱  
 [Procedures](../Topic/Procedures%20in%20Visual%20Basic.md)   
 [Procedure Parameters and Arguments](../Topic/Procedure%20Parameters%20and%20Arguments%20\(Visual%20Basic\).md)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)