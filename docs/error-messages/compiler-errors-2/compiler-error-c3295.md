---
title: 編譯器錯誤 C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 4ee79e87085b0b939a762fec4c576c393846c2ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756860"
---
# <a name="compiler-error-c3295"></a>編譯器錯誤 C3295

'#pragma pragma' 只能使用在全域或命名空間範圍

有些 pragma 無法用於函式中。  如需詳細資訊，請參閱 Pragma 指示詞[和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

## <a name="example"></a>範例

下列範例會產生 C3295。

```cpp
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```
