---
title: 編譯器警告 （層級 4） C4214 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4214
dev_langs:
- C++
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 879c959bfe851b56dbc60b4eeb714db8d7f9dfaf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027423"
---
# <a name="compiler-warning-level-4-c4214"></a>編譯器警告 (層級 4) C4214

使用非標準擴充： 位元非整數的欄位類型

使用預設的 Microsoft 擴充功能 (/Ze) 中，位元欄位的結構成員可以是任何整數類型。

## <a name="example"></a>範例

```
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

這類的位元欄位是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。