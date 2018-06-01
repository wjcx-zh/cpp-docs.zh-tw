---
title: 編譯器錯誤 C2393 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2393
dev_langs:
- C++
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 057537c8efcf6e827d9ac9aaf36c0eace6d24156
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704026"
---
# <a name="compiler-error-c2393"></a>編譯器錯誤 C2393

> '*符號*': per-appdomain 符號不可配置在區段'*區段*'

## <a name="remarks"></a>備註

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

使用[appdomain](../../cpp/appdomain.md)變數表示您使用編譯 **/clr: pure**或 **/clr: safe**，和安全或純粹的映像不能包含的資料區段。

請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C2393。 若要修正此問題，請勿建立的資料區段。

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```