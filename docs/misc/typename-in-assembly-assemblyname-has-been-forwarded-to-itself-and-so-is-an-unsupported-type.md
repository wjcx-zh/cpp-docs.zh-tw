---
title: "組件 &#39;&lt;組件名稱&gt;&#39; 中的 &#39;&lt;類型名稱&gt;&#39; 已轉送至其本身，所以不支援該類型 | Microsoft Docs"
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
  - "bc31425"
  - "vbc31425"
helpviewer_keywords: 
  - "BC31425"
  - "類型轉送"
ms.assetid: e3275d55-3f4c-4bbc-9c8f-f55c4e973063
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 組件 &#39;&lt;組件名稱&gt;&#39; 中的 &#39;&lt;類型名稱&gt;&#39; 已轉送至其本身，所以不支援該類型
組件使用 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 將它的其中一個類型轉送到另一個組件，但在相同組件中指定相同的類型。  
  
 *「類型轉送」*\(type forwarding\) 表示將類別、結構、介面、委派或列舉的定義，重新指派給不是原本定義所在的組件。 它通常會與*「程式碼重構」*\(code refactoring\) 一起使用，藉此您會將一個組件分割成兩個或更多個組件，或是將一個組件中的程式碼移到另一個。  
  
 轉送到類型本身會造成循環轉送。 如果另一個組件嘗試存取轉送的類型，它會經歷永無止盡的轉送，而永遠無法到達未轉送的類型。  
  
 **錯誤 ID︰**BC31425  
  
### 更正這個錯誤  
  
-   請將類型轉送至不同組件中的類型，或是完全不要轉送它。  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](../windows/type-forwarding-cpp-cli.md)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)