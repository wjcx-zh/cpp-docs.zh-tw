---
title: "編譯器錯誤 CS1110 | Microsoft Docs"
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
  - "CS1110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1110"
ms.assetid: 5b571a76-1891-4f33-b23d-7c4cc654a05f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1110
方法宣告的第一個參數如要使用 'this' 修飾詞，就必須參考 System.Core.dll。 加入對 System.Core.dll 的參考，或移除方法宣告中的 'this' 修飾詞。  
  
 3.5 版和更新版本的 .NET Framework 支援擴充方法。 擴充方法會產生以屬性標記方法的中繼資料。 屬性類別位於 system.core.dll。  
  
### 更正這個錯誤  
  
1.  如訊息所述，加入對 System.Core.dll 的參考，或移除方法宣告中的 `this` 修飾詞。  
  
## 範例  
 下例會產生 CS1110，如果檔案未以 System.Core.dll 的參考編譯：  
  
```  
// cs1110.cs // CS1110 // Compile with: /target:library public static class Extensions { public static bool Test(this bool b) { return b; } }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)