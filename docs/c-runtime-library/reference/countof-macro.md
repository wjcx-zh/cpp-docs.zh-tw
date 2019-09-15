---
title: _countof 巨集
ms.date: 03/22/2018
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 3debd63da7d218e29f31847034c69d89b4691643
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942682"
---
# <a name="_countof-macro"></a>_countof 巨集

計算靜態配置陣列中的元素數目。

## <a name="syntax"></a>語法

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>參數

*array*<br/>
陣列的名稱。

## <a name="return-value"></a>傳回值

陣列中的元素數目，以**size_t**表示。

## <a name="remarks"></a>備註

**_countof**會實作為類似函數的預處理器宏。 如果C++傳遞指標而非靜態宣告的陣列，版本會在編譯時期偵測額外的範本機制。

請確定*陣列*實際上是陣列，而不是指標。 在 C 中，如果*陣列*是指標， **_countof**會產生錯誤的結果。 在C++中，如果*陣列*是指標， **_countof**就無法編譯。  當做參數傳遞至*decays 指標*的函式陣列，這表示在函式內，您無法使用 **_countof**來判斷陣列的範圍。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>範例

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>另請參閱

[sizeof 運算子](../../cpp/sizeof-operator.md)<br/>
