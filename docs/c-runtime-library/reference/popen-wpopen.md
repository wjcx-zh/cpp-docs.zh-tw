---
title: _popen, _wpopen
description: Microsoft C runtime （CRT）程式庫函數_popen和_wpopen的參考。
ms.date: 4/2/2020
api_name:
- _popen
- _wpopen
- _o__popen
- _o__wpopen
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
no-loc:
- _popen
- _wpopen
- _tpopen
- _doserrno
- errno
- _sys_errlist
- _sys_nerr
- EINVAL
ms.openlocfilehash: 37e5bb491234e46a0e3330bc2fd42c16e54793fc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915282"
---
# <a name="_popen-_wpopen"></a>_popen、_wpopen

建立管道並執行命令。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>參數

*命令*\
要執行的命令。

*下*\
所傳回資料流的模式。

## <a name="return-value"></a>傳回值

傳回與所建立管道的一端相關聯的資料流。 管道的另一端會與所繁衍命令的標準輸入或標準輸出相關聯。 發生錯誤時，函式會傳回 **NULL**。 如果錯誤是由不正確參數所造成，則**errno**會設定為**EINVAL**。 請參閱＜備註＞一節查看有效的模式。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Popen**函數會建立一個管道。 然後，它會以非同步方式執行命令處理器的產生複本，並使用*命令*做為命令列。 字元字串 *mode* 會指定要求的存取類型，如下所示。

|存取模式|描述|
|-|-|
|**r**|呼叫處理序可使用傳回的資料流來讀取繁衍命令的標準輸出。|
|**寬**|呼叫處理序可使用傳回的資料流來寫入至繁衍命令的標準輸入。|
|**位元組**|在二進位模式中開啟。|
|**而已**|在文字模式中開啟。|

> [!NOTE]
> 如果在 Windows 程式中使用， **_popen**函式會傳回不正確檔案指標，使程式無限期地停止回應。 **_popen**在主控台應用程式中正常運作。 若要建立重新導向輸入和輸出的 Windows 應用程式，請參閱在 Windows SDK 中[使用重新導向的輸入和輸出建立子進程](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output)。

**_wpopen**是寬字元版本的 **_popen**;**_wpopen**的*path*引數是寬字元字串。 相反地， **_wpopen**和 **_popen**的行為相同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      puts(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

此輸出假設目前目錄中只有一個檔案具有`.c`副檔名。

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>另請參閱

[進程和環境控制](../../c-runtime-library/process-and-environment-control.md)\
[_pclose](pclose.md)\
[_pipe](pipe.md)
