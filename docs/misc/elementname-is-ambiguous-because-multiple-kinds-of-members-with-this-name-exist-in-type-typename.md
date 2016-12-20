---
title: "&#39;&lt;項目名稱&gt;&#39; 模稜兩可，因為在 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中有多種具有這個名稱的成員 | Microsoft Docs"
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
  - "bc31429"
  - "vbc31429"
helpviewer_keywords: 
  - "BC31429"
ms.assetid: fdc92c16-934d-47c0-9c44-332cbd58b73b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;項目名稱&gt;&#39; 模稜兩可，因為在 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中有多種具有這個名稱的成員
運算式存取了定義於類別、結構、模組或介面的程式設計項目，但該項目包含多個具有相同名稱的成員。  
  
 這個錯誤最可能的原因是*「區分大小寫」*\(case sensitivity\)。 Visual Basic 名稱不區分大小寫，這表示您可以在程式碼中的不同位置使用大小寫不同的名稱。 例如，如果您定義名稱為 `XYZ` 的變數，並於稍後以 `xyz` 存取，編譯器會將這兩個名稱視為相等。  
  
 不過，其他語言 \(例如 [C\#](../Topic/C%23.md) 和 [Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)\) 則區分大小寫。 在這類語言中，`XYZ` 和 `xyz` 不會被視為相同的名稱。 因此，以這類語言撰寫的類別可定義名為 `XYZ` 的變數和名為 `xyz` 的屬性。 Common Language Runtime \(CLR\) 會保留組件中的區分大小寫。 不過，如果 Visual Basic 應用程式以名稱 `XYZ` 和 `xyz` 來存取組件，則會顯示為相同名稱。  
  
 **錯誤 ID︰**BC31429  
  
### 更正這個錯誤  
  
1.  如果您可以控制定義類型的原始程式碼，請考慮重新命名成員，使其不只是大小寫不同而已。 如果已發行定義類型並正由其他應用程式使用中，則可能無法執行這項作業。  
  
2.  如果您無法在定義類型中重新命名成員，請從您的程式碼中移除引用的程式設計項目。 您無法存取 Visual Basic 中似乎有多個定義的項目。  
  
## 請參閱  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [為變數進行疑難排解](../Topic/Troubleshooting%20Variables%20in%20Visual%20Basic.md)   
 [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)