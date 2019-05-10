---
title: 編譯器錯誤 C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e4540180058c890a1dec9c4060f796f1f044c934
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447990"
---
# <a name="compiler-error-c2603"></a>編譯器錯誤 C2603

> '*函式*':太多區塊範圍靜態物件以建構函式/解構函式在函式

在版本的 MicrosoftC++編譯器之前 Visual Studio 2015 中，或當[/zc: threadsafeinit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)編譯器選項指定，則為 31，您可以在外部可見的靜態物件的數目限制內嵌函式。

若要解決此問題，我們建議您採用較新版本的 MicrosoftC++編譯器工具組，或可能的話，請移除 /zc: threadsafeinit 編譯器選項。 如果這不可行，請考慮結合您靜態物件。 如果物件相同類型，請考慮使用單一的靜態陣列，該型別，並參考所需的個別成員。

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
