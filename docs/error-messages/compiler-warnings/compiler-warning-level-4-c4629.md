---
title: 編譯器警告 (層級 4) C4629
ms.date: 11/04/2016
f1_keywords:
- C4629
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
ms.openlocfilehash: db3f4201dbf5ff925449b0924d08a43ee4283b3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651785"
---
# <a name="compiler-warning-level-4-c4629"></a>編譯器警告 (層級 4) C4629

使用了雙拼詞，字元順序 'digraph' 被解譯為語彙基元 'char' (如果這不是您想要的，請在兩個字元之間插入一個空格)

在 [/Za](../../build/reference/za-ze-disable-language-extensions.md)下，偵測到雙拼詞時，編譯器會發出警告。

下列範例會產生 C4629：

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```