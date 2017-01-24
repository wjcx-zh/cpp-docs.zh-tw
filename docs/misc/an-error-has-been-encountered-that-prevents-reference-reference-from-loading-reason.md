---
title: "An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt;
從專案檔移除參考時，發生嚴重錯誤。  您可在 \<reason\> 中找到這個錯誤的原因，可能的原因有：  
  
-   參考的 GUID 不正確。  這只適用 COM 參考。  
  
-   錯誤的包裝函式工具。  目前，包裝函式工具屬性 \(Property\) 可以是 tlbimp、aximp 或 primary 其中之一。  這只適用 COM 參考。  
  
-   錯誤的專案參考字串。  這只適用 project\-to\-project 參考。  
  
 **若要更正這個錯誤**  
  
-   將參考加入至專案以解決這個問題。  
  
     任何出現這項診斷的參考將不會被載入專案。  
  
## 請參閱  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)