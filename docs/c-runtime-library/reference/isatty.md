---
title: _isatty
ms.date: 4/2/2020
api_name:
- _isatty
- _o__isatty
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: c9611c2bd55ebc1602a73e4c71518716ea100420
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343908"
---
# <a name="_isatty"></a>_isatty

判斷檔案描述元是否與字元裝置相關聯。

## <a name="syntax"></a>語法

```C
int _isatty( int fd );
```

### <a name="parameters"></a>參數

*Fd*<br/>
參照至需要測試之裝置的檔案描述元。

## <a name="return-value"></a>傳回值

如果描述元與字元設備關聯 **,_isatty**返回非零值。 否則 **,_isatty**返回 0。

## <a name="remarks"></a>備註

**_isatty**功能確定*fd*是否與字元設備(終端、控制台、印表機或串行埠)相關聯。

此函數驗證*fd*參數。 如果*fd*是錯誤的檔指標,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回 0 並將**errno**設定到**EBADF**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_isatty**|\<io.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
