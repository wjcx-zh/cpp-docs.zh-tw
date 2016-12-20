---
title: "編譯器警告 (層級 1) CS0688 | Microsoft Docs"
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
  - "CS0688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0688"
ms.assetid: 8ce5af36-663e-46e8-87e9-bb32555796ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0688
'method1' 有連結需求，但是會覆寫或實作沒有連結需求的 'method2'。 可能會產生安全性弱點。  
  
 藉由呼叫基底類別方法，即可輕鬆地規避衍生類別方法上所設定的連結需求。 若要關閉安全性漏洞，基底類別方法也必須使用連結需求。 如需詳細資訊，請參閱 [Demand 和LinkDemand 的比較](http://msdn.microsoft.com/zh-tw/1ab877f2-70f4-4e0d-8116-943999dfe8f5)。  
  
## 範例  
 下列範例會產生 CS0688。 若要在不修改基底類別的情況下解決警告，請從覆寫方法中移除安全性屬性。 這不會解決安全性問題。  
  
```  
// CS0688.cs // compile with: /W:1 using System; using System.Security.Permissions; class Base { //Uncomment the following line to close the security hole //[FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] public virtual void DoScaryFileStuff() { } } class Derived: Base { [FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] // CS0688 public override void DoScaryFileStuff() { } static void Main() { } }  
```