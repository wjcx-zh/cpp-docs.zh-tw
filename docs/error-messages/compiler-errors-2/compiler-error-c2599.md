---
title: 編譯器錯誤 C2599
ms.date: 11/04/2016
f1_keywords:
- C2599
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
ms.openlocfilehash: c722335660653df7e533ec25d4708f42c16846ef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740763"
---
# <a name="compiler-error-c2599"></a>編譯器錯誤 C2599

' enum '：不允許列舉類型的向前宣告

編譯器不再支援 managed 列舉的向前宣告。

在[/za](../../build/reference/za-ze-disable-language-extensions.md)下，不允許使用列舉類型的向前宣告。

下列範例會產生 C2599：

```cpp
// C2599.cpp
// compile with: /clr /c
enum class Status;   // C2599

enum class Status2 { stop2, hold2, go2};

ref struct MyStruct {
   // Delete the following line to resolve.
   Status m_status;

   Status2 m_status2;   // OK
};

enum class Status { stop, hold, go };
```
