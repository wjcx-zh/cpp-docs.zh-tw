---
title: 編譯器錯誤 C3891
ms.date: 11/04/2016
f1_keywords:
- C3891
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
ms.openlocfilehash: 4b5ef8b837033a149455c040f748f479aa3f424d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736395"
---
# <a name="compiler-error-c3891"></a>編譯器錯誤 C3891

' var '：常值資料成員不能用來做為左值

[常](../../extensions/literal-cpp-component-extensions.md)值變數是 const，而且在宣告中初始化之後，其值不能變更。

下列範例會產生 C3891：

```cpp
// C3891.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3891
}
```
