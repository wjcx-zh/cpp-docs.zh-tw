---
title: 編譯器警告 (層級 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: 11c6b1ad50c44ac4ad2a9d014e57efef097d9d8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401172"
---
# <a name="compiler-warning-level-4-c4208"></a>編譯器警告 (層級 4) C4208

使用非標準擴充： delete [exp]-exp 予以評估但忽略

搭配 Microsoft 擴充功能 (/Ze)，您可以刪除使用以括號括住值的陣列[delete 運算子](../../cpp/delete-operator-cpp.md)。 會忽略的值。

```
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

這類值都無效 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。