---
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: d705029c30fdbc117c4c6e96923691e43e072e23
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221070"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft 專屬**

提供保留目前函式之傳回位址的記憶體位置位址。 此位址不得用來存取其他記憶體位置 (例如函式的引數)。

## <a name="syntax"></a>語法

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86、x64、ARM、ARM64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

在`_AddressOfReturnAddress`以[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯`_AddressOfReturnAddress`的程式中使用時, 包含呼叫的函式會編譯成原生函式。 當編譯為 managed 呼叫包含`_AddressOfReturnAddress`之函式的函式時, `_AddressOfReturnAddress`可能不會如預期般運作。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
