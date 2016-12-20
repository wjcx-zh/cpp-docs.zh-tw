---
title: "編譯器警告 (層級 1) CS1684 | Microsoft Docs"
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
  - "CS1684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1684"
ms.assetid: 620419bf-b6d5-4cda-a549-fcacf2f08920
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1684
類型 'Type Name' 的參考表示它是在 'Namespace' 中定義的，但是找不到  
  
 造成這個錯誤的原因，可能是一個命名空間中的參考參考到第二個命名空間中指出存在的類型，但該類型不存在。 例如，mydll.dll 指出 yourdll.dll 中有類型 `A`，但 yourdll.dll 中沒有這種類型。 這個錯誤的一個可能原因是您使用的 yourdll.dll 版本太舊，因此尚未定義 `A`。  
  
 下列範例會產生 CS1684。  
  
## 範例  
  
```  
// CS1684_a.cs // compile with: /target:library /keyfile:CS1684.key public class A { public void Test() {} } public class C2 {}  
```  
  
## 範例  
  
```  
// CS1684_b.cs // compile with: /target:library /r:cs1684_a.dll // post-build command: del /f CS1684_a.dll using System; public class Ref { public static A GetA() { return new A(); } public static C2 GetC() { return new C2(); } }  
```  
  
## 範例  
 我們現在將重建第一個組件，但略過不要在重新編譯中定義的類別 C2 定義。  
  
```  
// CS1684_c.cs // compile with: /target:library /keyfile:CS1684.key /out:CS1684_a.dll public class A { public void Test() {} }  
```  
  
## 範例  
 這個模組透過識別項 `Ref` 參考第二個模組。 但是，第二個模組包含類別 `C2` 的參考，此類別由於上一個步驟中的編譯已不存在，因此編譯這個模組會傳回 CS1684 錯誤訊息。  
  
```  
// CS1684_d.cs // compile with: /reference:cs1684_a.dll /reference:cs1684_b.dll // CS1684 expected class Tester { public static void Main() { Ref.GetA().Test(); } }  
```