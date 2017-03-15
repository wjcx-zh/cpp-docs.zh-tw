---
title: "嚴重錯誤 C1017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1017"
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 嚴重錯誤 C1017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無效的整數常數運算式  
  
 `#if` 指示詞中的運算式不存在，或是沒有評估出一個常數。  
  
 使用 `#define` 定義的常數如果被用在 `#if`、`#elif` 或 `#else` 指示詞，便必須是評估成整數常數的值。  
  
 下列範例會產生 C1017：  
  
```  
// C1017.cpp  
#define CONSTANT_NAME "YES"  
#if CONSTANT_NAME   // C1017  
#endif  
```  
  
 可能的解決方案：  
  
```  
// C1017b.cpp  
// compile with: /c  
#define CONSTANT_NAME 1  
#if CONSTANT_NAME  
#endif  
```  
  
 因為 `CONSTANT_NAME` 評估出字串，而不是整數，`#if` 指示詞將產生嚴重錯誤 C1017。  
  
 在其他狀況，前置處理器 \(Preprocessor\) 會將未定義的常數評估成零。  這可能會產生像下列範例所示的非預期結果。  因為 `YES` 並未定義，故將其評估成零。  `#if` `CONSTANT_NAME` 運算式評估出 False，而前置處理器已經移除了用於 `YES` 的程式碼。  `NO` 也尚未定義 \(零\)，因此 `#elif` `CONSTANT_NAME==NO` 將評估成 True \(`0 == 0`\)，導致前置處理器將程式碼留在陳述式的 `#elif` 部分─這和您預期的結果完全相反。  
  
```  
// C1017c.cpp  
// compile with: /c  
#define CONSTANT_NAME YES  
#if CONSTANT_NAME  
   // Code to use on YES...  
#elif CONSTANT_NAME==NO  
   // Code to use on NO...  
#endif  
```  
  
 若要確實檢視編譯器處理前置處理器指示詞的方式，請使用 [\/P](../../build/reference/p-preprocess-to-a-file.md)、[\/E](../../build/reference/e-preprocess-to-stdout.md) 或 [\/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)。