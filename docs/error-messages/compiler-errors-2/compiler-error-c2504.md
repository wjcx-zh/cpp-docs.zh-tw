---
title: 編譯器錯誤 C2504 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fb11774f65454799761913babb428dc6a471743
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054125"
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