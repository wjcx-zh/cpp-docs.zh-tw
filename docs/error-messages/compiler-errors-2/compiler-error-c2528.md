---
title: 編譯器錯誤 C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: 890dae7aa34103bde0168f1933bb42343d84100b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408578"
---
# <a name="compiler-error-c2528"></a>編譯器錯誤 C2528

'name': 參考的指標不合法

您無法宣告為參考的指標。 之前宣告的指標取值的變數。

下列範例會產生 C2528:

```
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```