---
title: _isatty
ms.date: 11/04/2016
api_name:
- _isatty
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: 2d2ba2fdfeb1c8bffe47b0953f0629746d2eb599
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954560"
---
# <a name="_isatty"></a>_isatty

判斷檔案描述元是否與字元裝置相關聯。

## <a name="syntax"></a>語法

```C
int _isatty( int fd );
```

### <a name="parameters"></a>參數

*fd*<br/>
參照至需要測試之裝置的檔案描述元。

## <a name="return-value"></a>傳回值

如果描述元與字元裝置相關聯， **_isatty**會傳回非零值。 否則， **_isatty**會傳回0。

## <a name="remarks"></a>備註

**_Isatty**函數會決定*fd*是否與字元裝置（終端機、主控台、印表機或序列埠）相關聯。

此函式會驗證*fd*參數。 如果*fd*是錯誤的檔案指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回0，並將**errno**設為**EBADF**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_isatty**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>範例輸出

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
