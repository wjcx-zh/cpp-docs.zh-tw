---
title: 編譯器錯誤 C3363
ms.date: 11/04/2016
f1_keywords:
- C3363
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
ms.openlocfilehash: eca598233dbe4cae4730e952b45945653ec8ffaa
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775500"
---
# <a name="compiler-error-c3363"></a>編譯器錯誤 C3363

'type': 'typeid' 只可套用至類型

已不正確地使用 [typeid](../../extensions/typeid-cpp-component-extensions.md) 運算子。

## <a name="example"></a>範例

下列範例會產生 C3363。

```
// C3363.cpp
// compile with: /clr
int main() {
   System::typeid;   // C3363
}
```