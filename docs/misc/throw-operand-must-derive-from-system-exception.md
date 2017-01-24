---
title: "&#39;Throw&#39; 運算元必須衍生自 &#39;System.Exception&#39; | Microsoft Docs"
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
  - "vbc30665"
  - "bc30665"
helpviewer_keywords: 
  - "BC30665"
ms.assetid: 7c228087-39ea-4b30-a410-6ba711e67e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Throw&#39; 運算元必須衍生自 &#39;System.Exception&#39;
提供給 `Throw` 的引數必須是 `System.Exception` 的執行個體，或衍生自 `System.Exception` 的類別的執行個體。  
  
 **錯誤 ID：**BC30665  
  
### 更正這個錯誤  
  
-   請使用衍生自 `System.Exception` 的引數，如下列範例所示。  
  
    ```  
    Throw New System.Exception("This is an error.")  
    ```  
  
## 請參閱  
 [Throw Statement](../Topic/Throw%20Statement%20\(Visual%20Basic\).md)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 中的例外狀況類別](http://msdn.microsoft.com/zh-tw/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)