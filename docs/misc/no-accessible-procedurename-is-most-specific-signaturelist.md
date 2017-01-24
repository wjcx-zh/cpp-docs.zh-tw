---
title: "沒有可存取的 &#39;&lt;程序名稱&gt;&#39; 是最明確的：&lt;簽章清單&gt; | Microsoft Docs"
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
  - "vbc30794"
  - "BC30794"
helpviewer_keywords: 
  - "BC30794"
ms.assetid: 51d54cbb-b530-4661-9952-5ccc17e4220b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有可存取的 &#39;&lt;程序名稱&gt;&#39; 是最明確的：&lt;簽章清單&gt;
指派陳述式將多載程序的位址指派給委派變數，但編譯器無法解析多載版本。  
  
 當程式碼使用定義在數個多載版本的程序的位址時，編譯器必須決定要使用的多載。 它嘗試找出具有符合委派參數清單的單一參數清單版本。 如需詳細資訊，請參閱[Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)。  
  
 如果編譯器發現多個版本具有相符簽章的程序，它會產生此錯誤。 例如，這種情形可能發生在其中一個多載是泛型，且類型引數傳遞給它，提供與另一個多載相同的簽章。  
  
 **錯誤 ID︰**BC30794  
  
### 更正這個錯誤  
  
-   如果衝突的起因是一個泛型多載具有與另一個多載相同的簽章，請變更傳遞給該泛型多載的類型引數。  
  
## 請參閱  
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)