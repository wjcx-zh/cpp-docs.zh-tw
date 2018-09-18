---
title: 編譯器錯誤 C2461 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39d58b315fdd7e3c4e1899041cebf8400813ed40
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029295"
---
# <a name="compiler-error-c2461"></a>編譯器錯誤 C2461

> '*類別*': 建構函式語法遺漏型式參數

此類別的建構函式未指定任何的型式參數。 建構函式宣告必須指定的型式參數清單。 清單可以是空的。

若要修正此問題，請新增一組括號之後的宣告*類別*:: **類別*。

## <a name="example"></a>範例

下列範例示範如何修正問題 C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```