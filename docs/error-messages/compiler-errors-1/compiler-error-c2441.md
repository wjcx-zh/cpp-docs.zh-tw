---
title: 編譯器錯誤 C2441 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4224d9090f3ace43f61a10c599fafa78d21600
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705276"
---
# <a name="compiler-error-c2441"></a>編譯器錯誤 C2441

> '*變數*': 以 __declspec （process） 宣告的符號必須是 const 在 /clr: pure 模式

## <a name="remarks"></a>備註

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

根據預設，變數是每個應用程式網域下 **/clr: pure**。 變數標示`__declspec(process)`下 **/clr: pure**容易發生錯誤，如果在一個應用程式定義域中修改和讀取在另一個。

因此，編譯器，將每個變數是程序會強制執行`const`下 **/clr: pure**，只在所有應用程式定義域中的進行這些讀取。

如需詳細資訊，請參閱[程序](../../cpp/process.md)和[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C2441。

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```