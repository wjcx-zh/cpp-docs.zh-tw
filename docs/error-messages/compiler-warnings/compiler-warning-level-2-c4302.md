---
title: 編譯器警告 （層級 2） C4302 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4302
dev_langs:
- C++
helpviewer_keywords:
- C4302
ms.assetid: f5e1c939-e134-4cca-ba1e-9b15a81549ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31ff3bebf07d87b507a18998658966b2c5a789b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025577"
---
# <a name="compiler-warning-level-2-c4302"></a>編譯器警告 (層級 2) C4302

'conversion': 從 'type 1' 的截斷為 'type 2'

編譯器偵測到從較大的類型轉換為較小的類型。 資訊可能會遺失。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4302:

```
// C4302.cpp
// compile with: /W2
#pragma warning(default : 4302)
int main() {
   int i;
   char c = (char) &i;     // C4302
   short s = (short) &i;   // C4302
}
```