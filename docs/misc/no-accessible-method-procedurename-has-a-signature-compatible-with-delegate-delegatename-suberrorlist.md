---
title: "沒有任何可存取的方法 &#39;&lt;程序名稱&gt;&#39; 具有與委派 &#39;&lt;委派名稱&gt;&#39; 相容的簽章：&lt;次要錯誤清單&gt; | Microsoft Docs"
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
  - "bc30950"
  - "vbc30950"
helpviewer_keywords: 
  - "BC30950"
ms.assetid: c1938099-2c03-491e-b599-d0c43bf94baf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有任何可存取的方法 &#39;&lt;程序名稱&gt;&#39; 具有與委派 &#39;&lt;委派名稱&gt;&#39; 相容的簽章：&lt;次要錯誤清單&gt;
指派陳述式將程序的位址指派給委派變數，但編譯器找不到具有相符簽章之程序的版本。  
  
 程式碼使用程序的位址時，編譯器會嘗試尋找該程序的版本，而該程序的版本具有符合委派版本的參數清單。 如果程序定義在數個多載版本中，則編譯器會嘗試尋找具有相符簽章的單一版本。 如需詳細資訊，請參閱[Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)。  
  
 如果編譯器找不到任何具有相符簽章之程序的版本，則會產生這個錯誤。 例如，如果程序或委派為泛型，並將類型引數傳遞給它，因而提供給它與另一個簽章不相符的簽章，則可能會發生這種情形。  
  
 **錯誤 ID︰**BC30950  
  
### 更正這個錯誤  
  
1.  重新定義程序或委派，讓它們具有相符的參數清單。  
  
     \-或\-  
  
     使用與程序參數相符的參數清單來定義新的委派，或使用與委派參數相符的參數清單來定義新的程序。  
  
2.  如果程序或委派為泛型，則會將它傳遞給類型引數，進而導致其簽章符合另一個簽章。  
  
## 請參閱  
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)