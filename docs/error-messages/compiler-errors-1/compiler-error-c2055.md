---
title: 編譯器錯誤 C2055 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2055
dev_langs:
- C++
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6c63d79325417fbd9b1f451fb4a51f13957b4df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019338"
---
# <a name="compiler-error-c2055"></a>編譯器錯誤 C2055

預期的型式參數清單中，不是類型的清單

函式定義包含參數的型別清單，而不是型式參數清單。 ANSI C 要求的型式參數命名為，除非它們是 void 或省略符號 (`...`)。

下列範例會產生 C2055:

```
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```