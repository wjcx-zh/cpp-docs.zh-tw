---
title: "無法推斷擴充方法 &#39;&lt;方法名稱&gt;&#39; (定義於 &#39;&lt;類型名稱&gt;&#39; 中) 的類型參數 &#39;&lt;類型參數名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc36589"
  - "bc36589"
helpviewer_keywords: 
  - "BC36589"
ms.assetid: 4676a7a5-934b-4b74-b640-48065fc07e94
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法推斷擴充方法 &#39;&lt;方法名稱&gt;&#39; (定義於 &#39;&lt;類型名稱&gt;&#39; 中) 的類型參數 &#39;&lt;類型參數名稱&gt;&#39;
泛型擴充方法是在未提供類型引數清單的情況下所呼叫，而且其中一個類型引數的類型推斷失敗。  
  
 當您呼叫泛型程序時，通常會針對該程序所定義的每個類型參數提供類型引數。 不過，您可以選擇完全省略類型引數清單。 如果您這麼做，編譯器會嘗試從呼叫的內容推斷每個類型引數的類型。 如需詳細資訊，請參閱 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)中的＜類型推斷＞。  
  
 **錯誤 ID︰**BC36589  
  
### 更正這個錯誤  
  
-   請確定一般引數類型的類型推斷是與針對泛型程序所宣告的類型參數一致。  
  
     \-或\-  
  
-   呼叫具有完整類型引數清單的泛型程序，因此不需要類型推斷。  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)