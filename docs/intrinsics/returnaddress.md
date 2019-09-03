---
title: _ReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 2a830ff1e8a2c9551dec52cf10a3d5cf126bde3b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218054"
---
# <a name="_returnaddress"></a>_ReturnAddress

**Microsoft 專屬**

`_ReturnAddress`內建會在呼叫函式中提供指示的位址, 在控制項傳回給呼叫者之後, 將會執行此函式。

建立下列程式, 並在偵錯工具中逐步執行它。 當您逐步執行程式時, 請記下從`_ReturnAddress`傳回的位址。 然後, 在從使用的`_ReturnAddress`函式傳回之後, 立即[開啟如何:使用 [反組](/visualstudio/debugger/how-to-use-the-disassembly-window)解碼] 視窗, 並注意下一個要執行的指令的位址符合從`_ReturnAddress`傳回的位址。

內嵌之類的優化可能會影響傳回位址。 例如, 如果下面的範例程式是以[/Ob1](../build/reference/ob-inline-function-expansion.md)編譯, `inline_func`則會內嵌至呼叫`main`函式。 因此, `_ReturnAddress`從`inline_func`和`main`對的呼叫會產生相同的值。

在`_ReturnAddress`以[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯`_ReturnAddress`的程式中使用時, 包含呼叫的函式將會編譯成原生函式。 當編譯為 managed 呼叫包含`_ReturnAddress`之函式的函式時, `_ReturnAddress`可能無法如預期般運作。

## <a name="requirements"></a>需求

**標頭檔**\<intrin.h. h >

## <a name="example"></a>範例

```cpp
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

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
