---
title: 編譯器錯誤 C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 8f428699aa14cbd1f021a57ed8dcabefa8b24c16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165082"
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