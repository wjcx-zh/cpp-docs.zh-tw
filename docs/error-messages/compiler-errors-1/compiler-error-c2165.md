---
title: 編譯器錯誤 C2165
ms.date: 11/04/2016
f1_keywords:
- C2165
helpviewer_keywords:
- C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
ms.openlocfilehash: 1dadc56dafca056db9b4a14ab39127306b797f8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174753"
---
# <a name="compiler-error-c2165"></a>編譯器錯誤 C2165

'keyword': 無法修飾指向資料的指標

`__stdcall`、 `__cdecl`或 `__fastcall` 關鍵字嘗試修改資料的指標。

下列範例會產生 C2165：

```
// C2165.cpp
// compile with: /c
char __cdecl *p;   // C2165
char *p;   // OK
```