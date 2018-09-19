---
title: 編譯器錯誤 C2674 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2674
dev_langs:
- C++
helpviewer_keywords:
- C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1e8a3533d1f2ac7a309f89e52a03b3ff8a62dec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037732"
---
# <a name="compiler-error-c2674"></a>編譯器錯誤 C2674

此內容中不允許泛型宣告

泛型宣告不正確。 如需詳細資訊，請參閱[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C2674。

```
// C2674.cpp
// compile with: /clr /c
void F(generic <class T> ref class R1);   // C2674
generic <class T> ref class R2 {};   // OK
```