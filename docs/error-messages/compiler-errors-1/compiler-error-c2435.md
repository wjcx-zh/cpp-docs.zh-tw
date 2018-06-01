---
title: 編譯器錯誤 C2435 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2435
dev_langs:
- C++
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ddf078420da8aba170bbd21a0db775f9246cea4
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703638"
---
# <a name="compiler-error-c2435"></a>編譯器錯誤 C2435

> '*var*': 動態初始設定必須有 managed 的 CRT，不能以 /clr: safe 編譯

## <a name="remarks"></a>備註

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

通用的每個應用程式網域變數的初始設定需要編譯的 CRT `/clr:pure`，這不會產生可驗證的影像。

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