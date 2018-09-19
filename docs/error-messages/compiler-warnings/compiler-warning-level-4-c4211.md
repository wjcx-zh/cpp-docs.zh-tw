---
title: 編譯器警告 （層級 4） C4211 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4211
dev_langs:
- C++
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2c92ef68768f4a9f8ac606716d5ae53c4aa72e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048210"
---
# <a name="compiler-warning-level-4-c4211"></a>編譯器警告 (層級 4) C4211

使用非標準擴充： extern 重新定義為靜態

使用預設的 Microsoft 擴充功能 (/Ze) 中，您可以重新定義`extern`識別碼作為**靜態**。

## <a name="example"></a>範例

```
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

這類重新定義是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="see-also"></a>另請參閱


