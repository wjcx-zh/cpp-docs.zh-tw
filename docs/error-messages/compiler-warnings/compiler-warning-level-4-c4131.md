---
title: 編譯器警告 (層級 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 24872bb0b42de77dde358dc29f99826b41638628
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516047"
---
# <a name="compiler-warning-level-4-c4131"></a>編譯器警告 (層級 4) C4131

'function': 使用舊樣式的宣告子

指定的函式宣告不是原型形式。

舊樣式函式宣告應該轉換成原型形式。

下列範例示範舊樣式函式宣告：

```
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

下列範例示範原型形式：

```
void addrec( char *name, int id )
{ }
```