---
title: "編譯器錯誤 CS2036 | Microsoft Docs"
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
  - "CS2036"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2036"
ms.assetid: 44b73be4-b792-4735-bdbd-bd757ab22683
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2036
\/pdb 選項需要同時使用 \/debug 選項。  
  
 只會針對偵錯組建產生程式資料庫檔案。 因此，**\/pdb** 選項在零售組建中沒有意義。  
  
### 更正這個錯誤  
  
-   加入 **\/debug** 編譯器選項。  
  
-   移除 **\/pdb** 編譯器選項。  
  
## 範例  
 下列範例使用 **\/pdb** 選項但未使用 \/debug 選項進行編譯時，會產生 CS2036。  
  
```  
// cs2036.cs // Compile with: /pdb // CS2036 class Test { public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [\/pdb \(Specify Debug Symbol File\)](../Topic/-pdb%20\(C%23%20Compiler%20Options\).md)   
 [\/debug \(Emit Debugging Information\)](../Topic/-debug%20\(C%23%20Compiler%20Options\).md)