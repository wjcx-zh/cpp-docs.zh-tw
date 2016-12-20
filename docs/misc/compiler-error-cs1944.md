---
title: "編譯器錯誤 CS1944 | Microsoft Docs"
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
  - "CS1944"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1944"
ms.assetid: e5e2c018-9a7e-48ee-8dd3-98e3553777c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1944
運算式樹狀結構不可包含 unsafe 指標作業  
  
 運算式樹狀架構不支援指標類型，因為 <xref:System.Linq.Expressions.Expression%601.Compile%2A?displayProperty=fullName> 方法只能產生可驗證的程式碼。 請參閱註解。  
  
### 更正這個錯誤  
  
1.  當您嘗試建立運算式樹狀架構，請不要使用指標類型。  
  
## 範例  
 下列範例會產生 CS1944：  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 在某些情況下，運算式樹狀架構中可以有指標。 例如，請參考下列程式碼：  
  
 `Expression<Func\<int*[], int*[]>) e = (int*[] i)=>i;`  
  
 此程式碼是有效的運算式樹狀架構，因為沒有類型引數是指標類型。 它們是陣列的指標，而陣列不是指標類型。 此外，運算式樹狀架構的本文不會危害任何指標。  
  
## 請參閱  
 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md)