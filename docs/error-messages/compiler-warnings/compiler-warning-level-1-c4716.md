---
title: 編譯器警告 (層級 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 91e836c9bb606d7759206788d1e3abd63b293fa8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175307"
---
# <a name="compiler-warning-level-1-c4716"></a>編譯器警告 (層級 1) C4716

'function' 必須傳回值

給定的函式未傳回值。

只有傳回型別為 void 的函式可以使用 return 命令，而不含伴隨的傳回值。

呼叫此函式時，將會傳回未定義的值。

此警告會自動升級為錯誤。 如果您想要修改此行為，請使用[#pragma 警告](../../preprocessor/warning.md)。

下列範例會產生 C4716：

```cpp
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```
