---
title: _fileno
ms.date: 11/04/2016
apiname:
- _fileno
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
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: 682ab4b01a663bd9a6314138aa692b1c05b7437a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646601"
---
# <a name="fileno"></a>_fileno

取得與資料流相關聯的檔案描述項。

## <a name="syntax"></a>語法

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**_fileno**傳回檔案描述項。 不會傳回錯誤。 如果，則結果為未定義*資料流*未指定開啟的檔案。 如果資料流**NULL**， **_fileno**叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 若要繼續，此函數會傳回-1 和集合允許執行**errno**要**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

> [!NOTE]
> 如果**stdout**或是**stderr**無關 （例如，在沒有主控台視窗的 Windows 應用程式） 的輸出資料流，傳回的檔案描述元是-2。 在舊版本中，傳回的檔案描述元是 -1。 此變更可讓應用程式區分這個條件與錯誤。

## <a name="remarks"></a>備註

**_Fileno**常式會傳回目前與相關聯的檔案描述項*串流*。 此常式可當作函式和巨集來實作。 如需選擇其中一個實作的資訊，請參閱[選擇函式與巨集](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen、wfdopen](fdopen-wfdopen.md)<br/>
[_filelength、_filelengthi64](filelength-filelengthi64.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
f[reopen、_wfreopen](freopen-wfreopen.md)<br/>
