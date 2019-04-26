---
title: 編譯器錯誤 C2735
ms.date: 11/04/2016
f1_keywords:
- C2735
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
ms.openlocfilehash: 73d5f61b5f86153db74a970d97b4656fb662bdad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152445"
---
# <a name="compiler-error-c2735"></a>編譯器錯誤 C2735

型式參數的類型規範中不允許 'keyword' 關鍵字

關鍵字在此內容中無效。

下列範例會產生 C2735:

```
// C2735.cpp
void f(inline int){}   // C2735
```