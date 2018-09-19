---
title: 編譯器錯誤 C2735 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2735
dev_langs:
- C++
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 732b75c8988f879af230e0513a751b8cd9c4ae67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093114"
---
# <a name="compiler-error-c2735"></a>編譯器錯誤 C2735

型式參數的類型規範中不允許 'keyword' 關鍵字

關鍵字在此內容中無效。

下列範例會產生 C2735:

```
// C2735.cpp
void f(inline int){}   // C2735
```