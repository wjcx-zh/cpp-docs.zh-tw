---
title: 編譯器錯誤 C2979 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2979
dev_langs:
- C++
helpviewer_keywords:
- C2979
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66f43af14474c042d7a4a311bbe672394a2f2d1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053345"
---
# <a name="compiler-error-c2979"></a>編譯器錯誤 C2979

不支援在泛型中進行明確特製化

泛型類別宣告不正確。  請參閱[泛型](../../windows/generics-cpp-component-extensions.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C2979：

```
// C2979.cpp
// compile with: /clr /c
generic <>
ref class Utils {};   // C2979 error

generic <class T>
ref class Utils2 {};   // OK
```