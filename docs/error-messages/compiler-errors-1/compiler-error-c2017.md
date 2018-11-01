---
title: 編譯器錯誤 C2017
ms.date: 11/04/2016
f1_keywords:
- C2017
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
ms.openlocfilehash: f4a17557e5e4ca1eb3f69561c964c9bbe24bb70d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440361"
---
# <a name="compiler-error-c2017"></a>編譯器錯誤 C2017

不合法的逸出序列

逸出序列，例如 \t，出現在外的字元或字串常數。

下列範例會產生 C2017:

```
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

字串化運算子搭配包含逸出序列的字串時，可能會發生 C2017。

下列範例會產生 C2017:

```
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```