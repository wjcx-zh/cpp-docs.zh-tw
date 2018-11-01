---
title: 編譯器錯誤 C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 5cd7a83575da7ab2a30401406d0c2ccf6c1b603e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438528"
---
# <a name="compiler-error-c2435"></a>編譯器錯誤 C2435

> '*var*': 動態初始設定必須有受控的 CRT，不能以 /clr: safe 編譯

## <a name="remarks"></a>備註

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

通用的每個應用程式網域變數的初始設定需要編譯 CRT `/clr:pure`，這不會產生可驗證映像。

如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [處理序](../../cpp/process.md)。

## <a name="example"></a>範例

下列範例會產生 C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```