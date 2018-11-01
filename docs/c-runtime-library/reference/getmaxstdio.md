---
title: _getmaxstdio
ms.date: 11/04/2016
apiname:
- _getmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getmaxstdio
- getmaxstdio
helpviewer_keywords:
- files [C++], number open
- _getmaxstdio function
- getmaxstdio function
- open files, getting number
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
ms.openlocfilehash: ea8e516b4c0806230376ea52e399c9fa1f9a858a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618332"
---
# <a name="getmaxstdio"></a>_getmaxstdio

傳回允許在資料流 I/O 層級同時開啟的檔案數目。

## <a name="syntax"></a>語法

```C
int _getmaxstdio( void );
```

## <a name="return-value"></a>傳回值

傳回表示目前在允許的同時開啟檔案數目的數字**stdio**層級。

## <a name="remarks"></a>備註

使用[_setmaxstdio](setmaxstdio.md)來設定在允許同時開啟的檔案數目**stdio**層級。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getmaxstdio**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_setmaxstdio.c
// The program retrieves the maximum number
// of open files and prints the results
// to the console.

#include <stdio.h>

int main()
{
   printf( "%d\n", _getmaxstdio());

   _setmaxstdio(2048);

   printf( "%d\n", _getmaxstdio());
}
```

```Output
512
2048
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
