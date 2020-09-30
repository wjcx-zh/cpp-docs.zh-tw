---
title: 編譯器錯誤 C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 0860f4b860b370f96c2c29046b090d5b205c63ba
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509384"
---
# <a name="compiler-error-c2504"></a>編譯器錯誤 C2504

' class '：基底類別未定義

基類已宣告但從未定義過。  可能的原因：

1. 遺漏 include 檔。

1. 外部基底類別未使用 [extern](../../cpp/extern-cpp.md)宣告。

下列範例會產生 C2504：

```cpp
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

還行

```
class C{};
class D : public C {};
```
