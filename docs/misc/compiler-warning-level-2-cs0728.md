---
title: "編譯器警告 (層級 2) CS0728 | Microsoft Docs"
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
  - "CS0728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0728"
ms.assetid: ad6d860d-bac4-48f3-9eab-1efd2b6de6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0728
可能不正確地指派給了為 using 或 lock 陳述式引數的本機 'variable'。  本機原始值會發生 Dispose 呼叫或解除鎖定。  
  
 有許多情況，`using` 或 `lock` 區塊會導致暫時性的資源流失。 例如：  
  
 `thisType f = null;`  
  
 `using (f)`  
  
 `{`  
  
 `f = new thisType();`  
  
 `...`  
  
 `}`  
  
 在此例中，當 `using` 區塊完成執行，但在區塊內建立的 `thisType` 物件沒有被記憶體回收時 \(雖然最後還是會回收\)，會處置變數 `thisType` 的原始值，例如 null。  
  
 若要解決這個錯誤，請使用下列格式：  
  
 `using (thisType f = new thisType())`  
  
 `{`  
  
 `...`  
  
 `}`  
  
 在此例中，會處置新配置的 `thisType` 物件。  
  
## 範例  
 下列程式碼會產生警告 CS0728。  
  
```  
// CS0728.cs using System; public class ValidBase : IDisposable { public void Dispose() {  } } public class Logger { public static void dummy() { ValidBase vb = null; using (vb) { vb = null;  // CS0728 } vb = null; } public static void Main() { } }  
```