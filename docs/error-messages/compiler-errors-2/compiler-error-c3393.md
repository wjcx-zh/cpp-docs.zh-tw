---
title: 編譯器錯誤 C3393
ms.date: 11/04/2016
f1_keywords:
- C3393
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
ms.openlocfilehash: 0f6952de20c27a811b85694ae13892eff9231f83
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757536"
---
# <a name="compiler-error-c3393"></a>編譯器錯誤 C3393

條件約束子句中語法錯誤：'identifier' 不是類型

傳遞給條件約束的識別項必須是類型，但卻不是類型。  如需詳細資訊，請參閱[泛型型別參數的限制式 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3393：

```cpp
// C3393.cpp
// compile with: /clr /c
void MyInterface() {}
interface class MyInterface2 {};

generic<typename T>
where T : MyInterface   // C3393
// try the following line instead
// where T : MyInterface2
ref class R {};
```
