---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 沒有類型參數，因此不可以有類型引數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32045"
  - "vbc32045"
helpviewer_keywords: 
  - "BC32045"
ms.assetid: b86e784c-6718-4585-bd39-2f0982068828
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 沒有類型參數，因此不可以有類型引數
叫用非泛型類型時，宣告或指派陳述式包含 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md) 子句。  
  
 根據其定義，*「泛型類型」*\(generic type\) 是在您可以透過一或多個*「類型參數」*\(type parameter\) 指定之資料類型上操作的類別、結構、介面、程序或委派。 使用程式碼從這個泛型類型建立類型時，會為每個類型參數各提供一個*「類型引數」*\(type argument\)。 在建立類型的過程中，每個類型引數會取代所產生程式碼中每個出現的對應類型參數。  
  
 類型參數會使用括弧內的 `Of` 子句定義，而類型引數則透過括弧內的 `Of` 子句提供。`Of` 子句僅適用於處理泛型類型。  
  
 非泛型類型不接受類型參數，而且當您叫用此類型時，無法指定任何類型引數。  
  
 **錯誤 ID：**BC32045  
  
### 更正這個錯誤  
  
1.  檢查您在宣告或指派陳述式中所使用的類型拼字。  
  
2.  如果您叫用非泛型類型，請移除任何 `Of` 子句及其括弧。 請勿移除程序、委派或類別建構函式之標準引數清單前後的括弧。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [如何：使用泛型類別](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)