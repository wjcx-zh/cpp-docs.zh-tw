---
title: 編譯器警告 （層級 1） C4326 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cee18a9ccc807370cf2fb40748939f211a4ba52f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211000"
---
# <a name="compiler-warning-level-1-c4326"></a>編譯器警告 (層級 1) C4326

> 傳回的類型 '*函式*'應該是'*type1*' 而不是 '*type2*'

## <a name="remarks"></a>備註

函式傳回的型別以外*type1*。 例如，使用[/Za](../../build/reference/za-ze-disable-language-extensions.md)，**主要**未傳回**int**。

## <a name="example"></a>範例

下列範例會產生 C4326，並示範如何修正此問題：

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```