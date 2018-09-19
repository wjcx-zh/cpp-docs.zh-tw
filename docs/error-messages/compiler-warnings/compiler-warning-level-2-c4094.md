---
title: 編譯器警告 （層級 2） C4094 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4094
dev_langs:
- C++
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b9317cbc31ef8bddb14da11af1087a148fd3188
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078708"
---
# <a name="compiler-warning-level-2-c4094"></a>編譯器警告 （層級 2） C4094

未標記 ' token' 宣告沒有符號

編譯器偵測到使用未標記的結構、 等位或類別的空白宣告。 宣告會被忽略。

## <a name="example"></a>範例

```
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

這種情況會產生 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。