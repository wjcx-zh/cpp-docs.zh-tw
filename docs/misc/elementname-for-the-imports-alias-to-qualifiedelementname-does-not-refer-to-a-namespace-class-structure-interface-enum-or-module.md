---
title: "Imports 別名為 &#39;&lt;限定項目名稱&gt;&#39; 的 &#39;&lt;項目名稱&gt;&#39; 並未參考 Namespace、Class、Structure、Interface、Enum 或 Module | Microsoft Docs"
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
  - "bc30798"
  - "vbc30798"
helpviewer_keywords: 
  - "BC30798"
ms.assetid: bfa66627-516a-4955-977d-92372bcea090
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Imports 別名為 &#39;&lt;限定項目名稱&gt;&#39; 的 &#39;&lt;項目名稱&gt;&#39; 並未參考 Namespace、Class、Structure、Interface、Enum 或 Module
[Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md) 指定無法匯入的程式設計項目。  
  
 `Imports` 陳述式用來減少或移除項目名稱前面之限定字串的需求。 您可以在 `Imports` 陳述式本身中限定項目，以提供項目唯一宣告的明確路徑。 之後，您不需要限定項目的參考。  
  
 `Imports` 最常用於命名空間，但您也可以匯入類別、模組、結構、介面或列舉來允許其沒有長限定字串之項目的參考。  
  
 如需詳細資訊，請參閱 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)中＜匯入包含項目＞的內容。  
  
 **錯誤 ID︰**BC30798  
  
### 更正這個錯誤  
  
1.  檢查 `Imports` 陳述式之限定性條件字串中的項目拼寫，特別是本身為所限定項目之字串中的最後一個項目。  
  
2.  確認所限定項目為合格的類型 \(命名空間、類別、模組、結構、介面或列舉\)。 如果不是，請移除 `Imports` 陳述式。  
  
## 請參閱  
 [References and the Imports Statement](../Topic/References%20and%20the%20Imports%20Statement%20\(Visual%20Basic\).md)