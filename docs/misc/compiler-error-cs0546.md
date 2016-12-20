---
title: "編譯器錯誤 CS0546 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0546
'accessor' : 因為 'property' 沒有可覆寫的 set 存取子，所以無法覆寫  
  
 嘗試覆寫屬性的其中一個存取子方法失敗，因為無法覆寫存取子。 可能發生這個錯誤的原因有：  
  
-   基底類別屬性未宣告為 [virtual](../Topic/virtual%20\(C%23%20Reference\).md)。  
  
-   基底類別屬性未宣告您嘗試覆寫的 [get](../Topic/get%20\(C%23%20Reference\).md) 或 [set](../Topic/set%20\(C%23%20Reference\).md) 存取子。  
  
 如果您不想要覆寫基底類別屬性，則可以在衍生類別中的屬性之前使用 [new](../Topic/new%20\(C%23%20Reference\).md) 關鍵字。  
  
 如需詳細資訊，請參閱[使用屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0546，因為基底類別未宣告屬性的 set 存取子。  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## 請參閱  
 [屬性](../Topic/Properties%20\(C%23%20Programming%20Guide\).md)