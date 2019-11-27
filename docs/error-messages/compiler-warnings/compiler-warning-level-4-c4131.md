---
title: 編譯器警告 (層級 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 266d62126d9154cd87706d3124e69e107bbdefde
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541582"
---
# <a name="compiler-warning-level-4-c4131"></a>編譯器警告 (層級 4) C4131

'function': 使用舊樣式的宣告子

指定的函式宣告不是原型形式。

舊樣式函式宣告應該轉換成原型形式。

下列範例示範舊樣式函式宣告：

```c
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

下列範例示範原型形式：

```c
void addrec( char *name, int id )
{ }
```