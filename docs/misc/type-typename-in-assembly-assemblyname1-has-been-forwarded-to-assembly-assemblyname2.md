---
title: "組件 &#39;&lt;組件名稱1&gt;&#39; 中的類型 &#39;&lt;類型名稱&gt;&#39; 已轉送至組件 &#39;&lt;組件名稱2&gt;&#39; | Microsoft Docs"
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
  - "vbc31424"
  - "bc31424"
helpviewer_keywords: 
  - "BC31424"
  - "類型轉送"
ms.assetid: 0f53e613-c1cb-4722-acb5-afa3091e277b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 組件 &#39;&lt;組件名稱1&gt;&#39; 中的類型 &#39;&lt;類型名稱&gt;&#39; 已轉送至組件 &#39;&lt;組件名稱2&gt;&#39;
組件 '\<組件名稱1\>' 中的類型 '\<類型名稱\>' 已轉送至組件 '\<組件名稱2\>'。 專案中遺漏對 '\<組件名稱2\>' 的參考，或者組件 '\<組件名稱2\>' 中遺漏類型 '\<類型名稱\>'。  
  
 組件原始程式碼中的運算式參考已轉送至另一個組件的類型，但在目的地組件中找不到該類型。  
  
 *「類型轉送」*\(type forwarding\) 表示將類別、結構、介面、委派或列舉的定義，重新指派給不是原本定義所在的組件。 它通常會與*「程式碼重構」*\(code refactoring\) 一起使用，藉此您會將一個組件分割成兩個或更多個組件，或是將一個組件中的程式碼移到另一個。  
  
 雖然類型暫時還可以用於原始組件中，但是當程式碼重構從原始組件中移除它時可能會變成未定義。  
  
 **錯誤 ID︰**BC31424  
  
### 更正這個錯誤  
  
-   確定類型存在於目的地組件中。  
  
-   確定專案具有對目的地組件的參考。  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](../windows/type-forwarding-cpp-cli.md)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)