---
title: 編譯器警告 (層級 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 9a7f42b2dd65644d3f2abec58236a0b93cc6f635
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653839"
---
# <a name="compiler-warning-level-1-c4269"></a>編譯器警告 (層級 1) C4269

'identifier': 'const' 編譯器產生預設建構函式初始化的自動資料會產生不可靠的結果

A **const**編譯器產生的預設建構函式初始化的非一般類別的自動執行個體。

## <a name="example"></a>範例

```
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

由於類別的這個執行個體產生在堆疊上的初始值`m_data`可以是任何項目。 此外，因為它是**const**執行個體的值`m_data`絕對不會變更。