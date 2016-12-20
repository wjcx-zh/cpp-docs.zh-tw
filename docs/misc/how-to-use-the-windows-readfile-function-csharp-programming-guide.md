---
title: "如何：使用 Windows ReadFile 函式 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ReadFile 函式 [C#]"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# 如何：使用 Windows ReadFile 函式 (C# 程式設計手冊)
此範例透過讀取和顯示文字檔示範 Windows `ReadFile` 函式。  `ReadFile` 函式需要使用 `unsafe` 程式碼，因為必須要有指標做為參數。  
  
 傳遞到 `Read` 函式的位元組陣列為 Managed 型別。  這表示 Common Language Runtime \(CLR\) 記憶體回收行程可依所需重新配置陣列使用的記憶體。  為了避免這一點，[fixed](../Topic/fixed%20Statement%20\(C%23%20Reference\).md) 會用來取得對記憶體的指標並加以標記，如此一來記憶體回收行程就不會移動它。  在 `fixed` 區塊的結尾，記憶體會自動回到遵從記憶體回收行程的移動。  
  
 這項功能稱為「*宣告式固定*」\(Declarative Pinning\)。  固定的好處在於虛耗的空間很少，除非記憶體回收發生在 `fixed` 區塊內，但實際上會發生的機率很低。  不過，固定可能在全域記憶體回收執行時，導致某些不想要的副作用。  記憶體回收行程壓縮記憶體的功能會大幅度受到固定緩衝區的限制。  因此，應盡量避免使用固定。  
  
## 範例  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../Topic/C%23%20Programming%20Guide.md)   
 [C\# 參考](../Topic/C%23%20Reference.md)   
 [Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)   
 [指標類型](../Topic/Pointer%20types%20\(C%23%20Programming%20Guide\).md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)