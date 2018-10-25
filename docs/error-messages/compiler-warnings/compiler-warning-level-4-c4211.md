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
ms.openlocfilehash: e38764970b8afde477c4f627e5cd3e5874d3b129
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054527"
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

