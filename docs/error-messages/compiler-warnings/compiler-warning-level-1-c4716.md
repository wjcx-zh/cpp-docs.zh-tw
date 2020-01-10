---
title: 編譯器警告（層級1） C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5215e8fd0bdd44c9bdfc731d2b74499d38853e80
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052467"
---
# <a name="compiler-warning-level-1-c4716"></a>編譯器警告（層級1） C4716

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