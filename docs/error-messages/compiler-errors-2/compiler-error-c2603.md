---
title: "編譯器錯誤 C2603 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2603
dev_langs: C++
helpviewer_keywords: C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c06c5747a3d785242e8b926fe6e1eaa251a2d8b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2603"></a>編譯器錯誤 C2603  
  
> '*函式*': 太多區塊範圍靜態物件的建構函式/解構函式在函式  
  
在 Visual Studio 2015 之前, 的 Visual c + + 編譯器的版本中或當[/zc: threadsafeinit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)指定編譯器選項時，31，您可以在外部可見的內嵌函式的靜態物件數目的限制.  
  
若要解決此問題，我們建議您採用較新版的 Visual c + + 編譯器工具組，或如果可能的話，移除 /zc: threadsafeinit-編譯器選項。 如果不可行，請考慮結合您的靜態物件。 如果相同型別的物件，請考慮使用單一的靜態陣列，該型別，並參考所需的個別成員。
  
## <a name="example"></a>範例  
  
下列程式碼會產生 C2603，並示範修正此問題的一種方法：  
  
```cpp  
// C2603.cpp  
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };  
extern inline void f1() {  
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;  
    static C C32;   // C2603 Comment this line out to avoid error  
}  
```
