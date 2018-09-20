---
title: _ReturnAddress |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c739590e5e208d9f83fa059f191ae80612a0dbd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380865"
---
# <a name="returnaddress"></a>_ReturnAddress

## <a name="microsoft-specific"></a>Microsoft 特定的

`_ReturnAddress`內建函式提供呼叫的函式，將控制項傳回給呼叫者之後執行指令的位址。

建立下列的程式和偵錯工具的逐步執行它。 當您逐步執行程式，請注意從傳回的位址`_ReturnAddress`。 然後，從函式傳回之後，立即所在`_ReturnAddress`已使用，請開啟[如何： 使用反組譯碼視窗](/visualstudio/debugger/how-to-use-the-disassembly-window)並記下一個要執行指令的位址符合從傳回的位址`_ReturnAddress`.

最佳化作業，例如內嵌的可能會影響傳回的位址。 例如，如果下面的範例程式會編譯[/Ob1](../build/reference/ob-inline-function-expansion.md)，`inline_func`會內嵌至呼叫的函式， `main`。 因此，呼叫`_ReturnAddress`從`inline_func`和`main`每個會產生相同的值。

當`_ReturnAddress`會在編譯的程式[/clr](../build/reference/clr-common-language-runtime-compilation.md)，函式包含`_ReturnAddress`呼叫將會編譯為原生函式。 當函式編譯為 managed 呼叫函式包含`_ReturnAddress`，`_ReturnAddress`可能無法如預期般運作。

## <a name="requirements"></a>需求

**標頭檔** \<intrin.h >

## <a name="example"></a>範例

```
// compiler_intrinsics__ReturnAddress.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_ReturnAddress)

__declspec(noinline)
void noinline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

__forceinline
void inline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

int main(void)
{
   noinline_func();
   inline_func();
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());

   return 0;
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)