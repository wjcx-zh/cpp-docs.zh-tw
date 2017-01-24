---
title: "多載解析失敗，因為沒有可存取的 &#39;&lt;方法&gt;&#39; 對這些引數而言是最適合的: &lt;錯誤&gt; | Microsoft Docs"
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
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "解析失敗"
  - "BC30521"
  - "多載解析失敗"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 多載解析失敗，因為沒有可存取的 &#39;&lt;方法&gt;&#39; 對這些引數而言是最適合的: &lt;錯誤&gt;
您已呼叫多載方法，但編譯器發現兩個或多個多載的參數清單，可供您的引數清單轉換，但無法從中選取。  
  
 編譯器會嘗試將呼叫引數清單中的資料類型，盡可能對應至多載參數清單中最接近的資料類型。 不論類型檢查參數 \([Option Strict Statement](../Topic/Option%20Strict%20Statement.md)\) 為 `On` 或 `Off`，您都必須將每個引數擴展轉換為其對應參數。  
  
 如果編譯器發現多個符合擴展需求的多載，則會尋找最適合引數資料類型的多載，也就是呼叫最少擴展的多載。 當某個多載比較適合某個引數的資料類型，而另一個多載比較適合另一個引數的資料類型時，就會產生這個錯誤訊息。 如需詳細資訊和範例，請參閱 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC30521  
  
### 更正這個錯誤  
  
1.  檢閱方法的所有多載，並決定要呼叫哪一個多載。  
  
2.  在您的呼叫陳述式中，將引數資料類型對應至為所需多載定義的參數資料類型。 您可能必須使用 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)，將一或多個資料類型轉換為定義的類型。  
  
## 請參閱  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Considerations in Overloading Procedures](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)   
 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Overloaded Properties and Methods](../Topic/Overloaded%20Properties%20and%20Methods%20\(Visual%20Basic\).md)   
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)