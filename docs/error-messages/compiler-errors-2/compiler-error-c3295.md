---
title: 編譯器錯誤 C3295 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3295
dev_langs:
- C++
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8210aacf60c4c53faf50278e7494c90c58aa67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076420"
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