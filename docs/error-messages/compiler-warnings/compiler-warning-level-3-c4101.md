---
title: 編譯器警告 （層級 3） C4101 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4101
dev_langs:
- C++
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1549a327329d438cb30bd6908e07419eb1b6bc1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060833"
---
# <a name="compiler-warning-level-3-c4101"></a>編譯器警告 （層級 3） C4101

'identifier': 未參考的區域變數

絕不會使用本機變數。 在明顯的情況下，會發生這個警告：

```
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

不過，這項警告也會發生時呼叫**靜態**透過類別的執行個體的成員函式：

```
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

在此情況下，編譯器會使用資訊的相關`si`若要存取**靜態**函式，但類別的執行個體不需要呼叫**靜態**函式，因此這項警告。 若要解決這個警告，您可以：

- 加入建構函式，編譯器會在其中使用的執行個體`si`的呼叫中`func`。

- 移除**靜態**定義中的關鍵字`func`。

- 呼叫**靜態**函式明確地： `int y = S::func();`。