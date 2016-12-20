---
title: "多載解析失敗，因為沒有可存取的 &#39;&lt;泛型程序名稱&gt;&#39; 接受此數目的類型引數 | Microsoft Docs"
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
  - "bc32087"
  - "vbc32087"
helpviewer_keywords: 
  - "BC32087"
ms.assetid: a3eaafd3-80f6-4b7d-9b75-47b043fe17b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 多載解析失敗，因為沒有可存取的 &#39;&lt;泛型程序名稱&gt;&#39; 接受此數目的類型引數
無法解析多載泛型程序的呼叫，因為編譯器無法存取任何具有適當數目之類型參數的多載版本。  
  
 當您呼叫泛型程序時，必須針對每個類型參數提供一個類型引數。 或者，您可以完全不提供類型引數，並讓編譯器嘗試進行*「類型推斷」*\(type inference\)。 如需詳細資訊，請參閱 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)中的＜類型推斷＞。  
  
 **錯誤 ID︰**BC32087  
  
### 更正這個錯誤  
  
1.  請確定呼叫端程式碼可存取您想要呼叫的版本。 請參閱 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)。  
  
2.  在呼叫端程式碼中加入或移除類型引數，讓類型引數清單符合您想要呼叫之版本的類型參數清單。  
  
     \-或\-  
  
     移除呼叫端程式碼中的所有類型引數，並讓編譯器嘗試進行類型推斷。 請注意，如果發生衝突或模稜兩可，則類型推斷可能會失敗。  
  
## 請參閱  
 [Overloaded Properties and Methods](../Topic/Overloaded%20Properties%20and%20Methods%20\(Visual%20Basic\).md)   
 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)