---
title: 編譯器錯誤 C2117 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2117
dev_langs:
- C++
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5579a6f05e1de768aebd2e68b64d0b861688607
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030976"
---
# <a name="compiler-error-c2117"></a>編譯器錯誤 C2117

'identifier': 陣列界限溢位

陣列中有太多的初始設定式：

- 陣列項目和初始設定式不相符的大小和數量。

- 給以 null 終止字串中沒有空間。

下列範例會產生 C2117:

```
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```