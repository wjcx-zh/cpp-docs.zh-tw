---
title: 編譯器錯誤 C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: 633ffa86bce3579adb808dbba34127bb6f0665c9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749408"
---
# <a name="compiler-error-c3895"></a>編譯器錯誤 C3895

' var '：類型資料成員不可為 ' volatile '

某些類型的資料成員（例如[常](../../extensions/literal-cpp-component-extensions.md)值或[initonly](../../dotnet/initonly-cpp-cli.md)）不能是[volatile](../../cpp/volatile-cpp.md)。

下列範例會產生 C3895：

```cpp
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```
