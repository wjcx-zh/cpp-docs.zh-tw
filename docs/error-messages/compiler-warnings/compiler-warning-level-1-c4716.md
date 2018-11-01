---
title: 編譯器警告 (層級 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5ec0aea543053d699db7483df7dd7ea91b3af715
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594541"
---
# <a name="compiler-warning-level-1-c4716"></a>編譯器警告 (層級 1) C4716

'function' 必須傳回值

指定的函式未傳回值。

唯一的函式傳回類型為 void 的可以使用傳回命令卻沒有隨附的傳回值。

呼叫此函式時，將會傳回未定義的值。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。

下列範例會產生 C4716:

```
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```