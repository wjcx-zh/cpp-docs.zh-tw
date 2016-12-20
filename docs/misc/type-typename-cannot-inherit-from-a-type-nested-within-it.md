---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 無法繼承自其內部的巢狀類型 | Microsoft Docs"
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
  - "bc30908"
  - "vbc30908"
helpviewer_keywords: 
  - "BC30908"
ms.assetid: bca164b2-a4a9-4ed4-9f71-a9a5a42f181a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 無法繼承自其內部的巢狀類型
類別或介面定義包含在其內指定巢狀類型的 [Inherits Statement](../Topic/Inherits%20Statement.md)。  
  
 繼承必須是線性，而非循環。 類型無法繼承自繼承它的類型。  
  
 相關的限制是類型無法繼承自尚未定義的類型。 繼承涉及重複使用基底類別成員的功能，因此需要定義這些成員。 因此，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法編譯程式碼 \(例如下列範例\)。  
  
```  
Public Class outerClass ' The following statement is INVALID because innerClass is not defined. Inherits innerClass Public Class innerClass Public Sub doSomething() End Sub End Class End Class  
```  
  
 **錯誤 ID︰**BC30908  
  
### 更正這個錯誤  
  
-   如果繼承類型 \(巢狀中的外部類型\) 必須繼承自內部類型，請將內部類型移出外部類型。  
  
-   如果內部類型必須巢狀於外部類型內，則外部類型無法繼承自它。 請移除 [Inherits Statement](../Topic/Inherits%20Statement.md)。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)