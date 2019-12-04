---
title: 編譯器錯誤 C3363
ms.date: 11/04/2016
f1_keywords:
- C3363
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
ms.openlocfilehash: 44b41dd706c7eb290c71d7312464d688cbcf08d3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757354"
---
# <a name="compiler-error-c3363"></a>編譯器錯誤 C3363

'type': 'typeid' 只可套用至類型

已不正確地使用 [typeid](../../extensions/typeid-cpp-component-extensions.md) 運算子。

## <a name="example"></a>範例

下列範例會產生 C3363。

```cpp
// C3363.cpp
// compile with: /clr
int main() {
   System::typeid;   // C3363
}
```
