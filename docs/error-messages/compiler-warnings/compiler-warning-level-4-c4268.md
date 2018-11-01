---
title: 編譯器警告 (層級 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: e3cda7ed70963508d7663c6c12b2b98ac64db204
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676495"
---
# <a name="compiler-warning-level-4-c4268"></a>編譯器警告 (層級 4) C4268

'identifier': 'const' 編譯器產生預設建構函式初始化的靜態/全域資料填滿零的物件

A **const**編譯器產生的預設建構函式初始化全域或靜態的重要類別的執行個體。

## <a name="example"></a>範例

```
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

因為這個類別的執行個體**const**，值`m_data`無法變更。