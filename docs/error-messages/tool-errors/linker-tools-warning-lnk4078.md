---
title: 連結器工具警告 LNK4078
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: 9ce72f476aa85434acd5277d0307ffc61e0a0214
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990996"
---
# <a name="linker-tools-warning-lnk4078"></a>連結器工具警告 LNK4078

找到多個具有不同屬性的「區段名稱」區段

連結找到兩個或多個具有相同名稱但屬性不同的區段。

此警告可能是由舊版連結或 LIB 所建立的匯入程式庫或匯出檔案所造成。

重新建立檔案，然後重新連結。

## <a name="example"></a>範例

LNK4078 也可能是由中斷性變更所造成： x86 上[init_seg](../../preprocessor/init-seg.md)所命名的區段是讀取/寫入，它現在是唯讀的。

下列範例會產生 LNK4078。

```cpp
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
