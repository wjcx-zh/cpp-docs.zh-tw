---
title: 編譯器警告 (層級 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: cc913a4f92963437347fbc708eca03c25ab9d403
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991475"
---
# <a name="compiler-warning-level-4-c4238"></a>編譯器警告 (層級 4) C4238

使用非標準的擴充：使用類別右值做為左值

為了與舊版的視覺效果C++相容，Microsoft extensions （ **/ze**）可讓您在隱含或明確接受其位址的內容中，使用類別類型做為右值。 在某些情況下（例如下列範例），這可能會造成危險。

## <a name="example"></a>範例

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

這種用法會導致 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下發生錯誤。
