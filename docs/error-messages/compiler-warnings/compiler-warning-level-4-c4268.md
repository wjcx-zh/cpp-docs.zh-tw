---
title: 編譯器警告 (層級 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: f3a6497ae7fc2bb3a73684c9dc76401cf96ca3fa
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991303"
---
# <a name="compiler-warning-level-4-c4268"></a>編譯器警告 (層級 4) C4268

' identifier '： ' const ' 靜態/全域資料使用編譯器所產生的預設函式會以零填滿物件

非一般類別的**常數**全域或靜態實例會使用編譯器產生的預設函式來初始化。

## <a name="example"></a>範例

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

因為這個類別的實例是**const**，所以無法變更 `m_data` 的值。
