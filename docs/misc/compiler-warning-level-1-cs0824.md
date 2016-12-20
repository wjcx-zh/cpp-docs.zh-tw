---
title: "編譯器警告 (層級 1) CS0824 | Microsoft Docs"
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
  - "CS0824"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0824"
ms.assetid: ad643bb7-51b2-455b-a9f3-2bd4588d2c5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0824
建構函式 'name' 標記為外部。  
  
 建構函式可能會標記為外部。 不過，編譯器無法驗證建構函式是否確實存在。 因此會產生警告。  
  
### 移除這個警告  
  
1.  請使用 pragma 警告指示詞來忽略它。  
  
2.  在類型內部移動建構函式。  
  
## 範例  
 下列程式碼會產生 CS0824：  
  
```  
// cs0824.cs public class C { extern C(); // CS0824 public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [extern](../Topic/extern%20\(C%23%20Reference\).md)   
 [\#pragma warning](../Topic/%23pragma%20warning%20\(C%23%20Reference\).md)