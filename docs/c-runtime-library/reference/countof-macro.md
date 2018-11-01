---
title: _countof 巨集
ms.date: 03/22/2018
apilocation:
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
apitype: DLLExport
f1_keywords:
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 60b4350d6cf14a545de67de0bdaee70ee2099006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536132"
---
# <a name="countof-macro"></a>_countof 巨集

計算靜態配置的陣列中的項目數。

## <a name="syntax"></a>語法

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>參數

*array*<br/>
陣列的名稱。

## <a name="return-value"></a>傳回值

在陣列中，以表示的項目數**size_t**。

## <a name="remarks"></a>備註

**_countof**會實作為函式類似前置處理器巨集。 C + + 版本中有額外的範本的機制，如果將指標傳遞而不是以靜態方式宣告陣列，在編譯時期偵測。

請確認*陣列*其實是一個陣列，不是指標。 在 C 中， **_countof**會產生錯誤的結果，如果*陣列*是指標。 C + + **_countof**無法編譯，如果*陣列*是指標。  陣列做為參數傳遞至函式*指標的 decays*，這表示在函式，您無法使用 **_countof**來判斷陣列的範圍。

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
