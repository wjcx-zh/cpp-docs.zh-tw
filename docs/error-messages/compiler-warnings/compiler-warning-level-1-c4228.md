---
title: 編譯器警告 （層級 1） C4228 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4228
dev_langs:
- C++
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab568ef6622bfa10f0e10566ec92dfaee71d22c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047950"
---
# <a name="compiler-warning-level-1-c4228"></a>編譯器警告 (層級 1) C4228

使用非標準擴充： 忽略宣告子清單中逗號後的限定詞

使用限定詞的要**const**或是`volatile`宣告變數時，逗號是 Microsoft 延伸模組之後 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>範例

```
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```