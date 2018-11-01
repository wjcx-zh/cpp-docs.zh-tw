---
title: 編譯器錯誤 C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 63739989d737527e3f136bb3aac2269eda6231c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601691"
---
# <a name="compiler-error-c3295"></a>編譯器錯誤 C3295

'#pragma pragma' 只能使用在全域或命名空間範圍

有些 pragma 無法用於函式中。  請參閱[Pragma 指示詞和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3295。

```
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```