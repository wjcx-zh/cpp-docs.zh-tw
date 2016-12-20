---
title: "編譯器警告 (層級 1) CS3006 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3006"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3006"
ms.assetid: efbfd898-e46f-4c3d-91e2-e2da0056b016
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3006
只有 ref\/out 或陣列陣序差異的多載方法 'method'，不符合 CLS 標準  
  
 方法無法根據 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 參數多載，而仍然符合 Common Language Specification \(CLS\)。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 CS3006： 若要解決這個警告，請將組件層級屬性標記為註解或移除其中一個方法定義。  
  
```  
// CS3006.cs using System; [assembly: CLSCompliant(true)] public class MyClass { public void f(int i) { } public void f(ref int i)   // CS3006 { } public static void Main() { } }  
```