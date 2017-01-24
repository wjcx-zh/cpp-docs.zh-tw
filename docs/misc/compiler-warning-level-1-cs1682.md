---
title: "編譯器警告 (層級 1) CS1682 | Microsoft Docs"
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
  - "CS1682"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1682"
ms.assetid: 6f3b19ba-29f3-4472-941d-57f6fda6dc3a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1682
類型 'type' 的參考表示它是以巢狀方式位於 'nested type' 內部，但是找不到  
  
 當您匯入與其他參考或您所撰寫的程式碼不一致的參考，就會發生這個錯誤。 最常發生這個錯誤的原因是撰寫參考中繼資料內類別的程式碼，接著您會刪除該類別，或修改其定義。  
  
## 範例  
  
```  
// CS1682.cs // compile with: /target:library /keyfile:mykey.snk public class A { public class N1 {} }  
```  
  
## 範例  
  
```  
// CS1682_b.cs // compile with: /target:library /reference:CS1682.dll using System; public class Ref { public static A A1() { return new A(); } public static A.N1 N1() { return new A.N1(); } }  
```  
  
## 範例  
  
```  
// CS1682_c.cs // compile with: /target:library /keyfile:mykey.snk /out:CS1682.dll public class A { public void M1() {} }  
```  
  
## 範例  
 下列範例會產生 CS1682。  
  
```  
// CS1682_d.cs // compile with: /reference:CS1682.dll /reference:CS1682_b.dll /W:1 // CS1682 expected class Tester { static void Main() { Ref.A1().M1(); } }  
```