---
title: 編譯器錯誤 C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: d47d99962d089d873cb9bbdf9baac7eab706fc16
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746886"
---
# <a name="compiler-error-c2504"></a>編譯器錯誤 C2504

' class '：基底類別未定義

基類已宣告，但從未定義過。  可能的原因:

1. 遺漏 include 檔案。

1. 外部基類未宣告為[extern](../../cpp/using-extern-to-specify-linkage.md)。

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
