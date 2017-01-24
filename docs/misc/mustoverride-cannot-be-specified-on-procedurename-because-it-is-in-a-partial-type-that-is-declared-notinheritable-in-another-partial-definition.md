---
title: "因為成員所屬的部分類型，在另一個部分定義中已宣告為 &#39;NotInheritable&#39;，所以無法在 &#39;&lt;程序名稱&gt;&#39; 指定 &#39;MustOverride&#39;。 | Microsoft Docs"
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
  - "vbc30927"
  - "BC30927"
helpviewer_keywords: 
  - "BC30927"
ms.assetid: 5798dfda-3d7b-4f30-9715-40cbf52d6dc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 因為成員所屬的部分類型，在另一個部分定義中已宣告為 &#39;NotInheritable&#39;，所以無法在 &#39;&lt;程序名稱&gt;&#39; 指定 &#39;MustOverride&#39;。
程序或屬性在多個部分宣告定義的類別內宣告為 `MustOverride`，但其中一個部分定義為類別指定 `NotInheritable`。  
  
 當您分割數個部分宣告中的類別定義時，編譯器會將類別視為其所有部分宣告的聯集。 這不只適用於成員，同時也適用於實作、繼承和存取層級。  
  
 若要覆寫程序或屬性，類別必須繼承其基底類別。 因此，若要為基底類別的程序或屬性指定 `MustOverride`，您必須為類別指定 `MustInherit`。 因為它們互相矛盾，所以您無法為同一個類別指定 `MustInherit` 和 `NotInheritable`。  
  
 **錯誤識別碼：**BC30927  
  
### 更正這個錯誤  
  
-   如果必須覆寫屬性或程序，則從其出現的部分宣告中移除 `NotInheritable` 關鍵字。  
  
-   如果類別必須是 `NotInheritable`，則從程序或屬性中移除 `MustOverride` 關鍵字。 因為您無法繼承類別，所以無法覆寫它。  
  
## 請參閱  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [MustOverride](../Topic/MustOverride%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)