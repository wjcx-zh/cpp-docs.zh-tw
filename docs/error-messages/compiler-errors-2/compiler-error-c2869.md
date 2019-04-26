---
title: 編譯器錯誤 C2869
ms.date: 11/04/2016
f1_keywords:
- C2869
helpviewer_keywords:
- C2869
ms.assetid: 6e30c001-47f3-4101-b9f1-cc542c9fffae
ms.openlocfilehash: 38ac73484814e0089b412938ffc2776872deff3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165550"
---
# <a name="compiler-error-c2869"></a>編譯器錯誤 C2869

'name': 已經定義為命名空間

您無法重複使用已使用的命名空間的名稱。

下列範例會產生 C2869:

```
// C2869.cpp
// compile with: /c
namespace A { int i; };

class A {};   // C2869, A is already used
```