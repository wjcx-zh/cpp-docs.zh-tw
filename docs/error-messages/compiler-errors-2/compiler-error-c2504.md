---
title: 編譯器錯誤 C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 8f428699aa14cbd1f021a57ed8dcabefa8b24c16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444387"
---
# <a name="compiler-error-c2504"></a>編譯器錯誤 C2504

'class': 基底類別未定義

基底類別已宣告但永遠不會定義。  可能的原因：

1. 遺漏 include 檔案。

1. 使用外部的基底類別未宣告[extern](../../cpp/using-extern-to-specify-linkage.md)。

下列範例會產生 C2504:

```
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

[確定]

```
class C{};
class D : public C {};
```