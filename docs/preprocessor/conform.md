---
title: "conform | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "conform_CPP"
  - "vc-pragma.conform"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "conform pragma"
  - "forScope conform pragma"
  - "Pragma, conform"
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# conform
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 指定 [\/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 編譯器選項的執行階段行為。  
  
## 語法  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### 參數  
 *name*  
 指定要修改的編譯器選項名稱。  唯一有效的 *name* 為 `forScope`。  
  
 **show** \(選擇性\)  
 在編譯期間透過警告訊息顯示 *name* \(true 或 false\) 的目前設定。  例如，`#pragma conform(forScope, show)`。  
  
 **on, off**\(選擇性\)  
 將 *name* 設定為 **on** 以啟用 [\/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 編譯器選項。  預設值是 **off**。  
  
 **push** \(選擇性\)  
 將 *name* 目前的值推入至內部編譯器堆疊。  如果指定了 *identifier*，則可以指定 **on** 或 **off** 值，以便將 *name* 推入堆疊上。  例如，`#pragma conform(forScope, push, myname, on)`。  
  
 **pop** \(選擇性\)  
 將 *name* 的值設定為內部編譯器堆疊頂端的值，然後再從堆疊中推出。  如果是使用 **pop** 指定識別項，則會將其推回堆疊中，直到找到具有 *identifier* 的記錄，此記錄也會從堆疊推出，而堆疊中下一個記錄內的 *name* 值將會變成 *name* 的新值。  如果指定要推出的 *identifier* 並不存在於堆疊上的記錄中，則會忽略 **pop**。  
  
 *identifier*\(選擇性\)  
 可以包含在 **push** 或 **pop** 命令中。  如果使用了 *identifier*，則也可以使用 **on** 或 **off** 指定名稱。  
  
## 範例  
  
```  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)