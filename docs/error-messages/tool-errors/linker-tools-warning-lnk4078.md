---
title: 連結器工具警告 LNK4078 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4078
dev_langs:
- C++
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eecd4dc17724b5c02a8ce8398f5630b691dab320
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109807"
---
# <a name="linker-tools-warning-lnk4078"></a>連結器工具警告 LNK4078

多個 '區段名稱' 區段有不同的屬性

連結找到兩個或更多具有相同的區段名稱但不同的屬性。

這個警告可能因舊版的連結] 或 [程式庫所建立的匯入程式庫或匯出檔案。

重新建立檔案並重新連結。

## <a name="example"></a>範例

LNK4078 也可能因一項重大變更： 所命名的區段[init_seg](../../preprocessor/init-seg.md) x86 上的 讀取/寫入，其現在為唯讀。

下列範例會產生 LNK4078。

```
// LNK4078.cpp
// compile with: /W1
// LNK4078 expected
#include <stdio.h>
#pragma warning(disable : 4075)
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // pointers to destructors.

struct A { A() {} };

int myexit (PF pf) { return 0; }

#pragma section(".mine$a", read, write)
// try the following line instead
// #pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) int ii = 1;

#pragma section(".mine$z", read, write)
// try the following line instead
// #pragma section(".mine$z", read)
__declspec(allocate(".mine$z")) int i = 1;

#pragma data_seg()
#pragma init_seg(".mine$m", myexit)
A bbbb;
A cccc;
int main() {}
```