---
title: _AddressOfReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: 678128c4b09b083b4afe3a86c9b2315eb3c87b1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584479"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft 專屬**

提供保存目前的函式的傳回位址的記憶體位置的位址。 此位址不可能用來存取其他記憶體位置 （例如，函式的引數）。

## <a name="syntax"></a>語法

```
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

當`_AddressOfReturnAddress`會在編譯的程式[/clr](../build/reference/clr-common-language-runtime-compilation.md)，函式包含`_AddressOfReturnAddress`呼叫會編譯為原生函式。 當函式編譯為 managed 呼叫函式包含`_AddressOfReturnAddress`，`_AddressOfReturnAddress`可能無法如預期般運作。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
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

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)