---
title: "編譯器錯誤 CS0837 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0837
"is" 或 "as" 運算子的第一個運算元不可以是 Lambda 運算式或匿名方法。  
  
 Lambda 運算式和匿名方法不能用於 [is](../Topic/is%20\(C%23%20Reference\).md) 或 [as](../Topic/as%20\(C%23%20Reference\).md) 的左邊。  
  
### 更正這個錯誤  
  
-   如果錯誤涉及 `is` 運算子，請記住 `is` 會使用值和類型，並告訴您是否可透過參考、Boxing 或 Unboxing 轉換將值改變為該類型。 因為 Lambda 不是值而且沒有參考、Boxing 或 Unboxing 轉換，所以 Lambda 不適合用於 `is`。  
  
-   如果程式碼誤用 `as`，則可能會進行更正，以將它變更為轉換。  
  
## 範例  
 下列範例會產生 CS0837：  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```