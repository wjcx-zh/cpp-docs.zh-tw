---
title: _countof Macro | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f30df64b045e2af6181d343a4eafb962d22eaa05
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394739"
---
# <a name="countof-macro"></a>_countof 巨集

計算靜態配置陣列中的項目數。

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

**_countof**實作為函式類似前置處理器巨集。 C + + 版本都有額外的範本機制，來偵測在編譯時期，如果將指標傳遞而不是以靜態方式宣告陣列。

請確認*陣列*其實是一個陣列，而非指標。 在 C 中， **_countof**會產生錯誤的結果，如果*陣列*的指標。 C + + **_countof**無法編譯如果*陣列*的指標。  陣列當做參數傳遞至函式*指標 decays*，這表示，在函式，您無法使用 **_countof**來判斷陣列的範圍。

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
