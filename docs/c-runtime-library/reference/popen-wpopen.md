---
title: _popen、_wpopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _popen
- _wpopen
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
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
dev_langs:
- C++
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a0dd4f32f8c7b3a9e859e23fcc26e668fa87cdb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726358"
---
# <a name="popen-wpopen"></a>_popen、_wpopen

建立管道並執行命令。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*command*<br/>
要執行的命令。

*mode*<br/>
所傳回資料流的模式。

## <a name="return-value"></a>傳回值

傳回與所建立管道的一端相關聯的資料流。 管道的另一端會與所繁衍命令的標準輸入或標準輸出相關聯。 發生錯誤時，函式會傳回 **NULL**。 如果錯誤是無效的參數，例如，如果*命令*或是*模式*為 null 指標，或*模式*而言不是有效的模式**errno**設為**EINVAL**。 請參閱＜備註＞一節查看有效的模式。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Popen**函式會建立一個管道，並以非同步方式執行命令處理器以指定字串的繁衍的複本*命令*。 字元字串 *mode* 會指定要求的存取類型，如下所示。

|存取模式|描述|
|-|-|
|**"r"**|呼叫處理序可使用傳回的資料流來讀取繁衍命令的標準輸出。|
|**"w"**|呼叫處理序可使用傳回的資料流來寫入至繁衍命令的標準輸入。|
|**"b"**|在二進位模式中開啟。|
|**"t"**|在文字模式中開啟。|

> [!NOTE]
> 如果在 Windows 程式中，使用 **_popen**函式會傳回無效的檔案指標，會造成程式無限期停止回應。 **_popen**在主控台應用程式中運作正常。 若要建立 Windows 應用程式會將重新導向輸入和輸出，請參閱[建立子處理序具有重新導向輸入和輸出](/windows/desktop/ProcThread/creating-a-child-process-with-redirected-input-and-output)Windows SDK 中。

**_wpopen**是寬字元版本的 **_popen**;*路徑*引數 **_wpopen**是寬字元字串。 **_wpopen**並 **_popen**行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
      printf(psBuffer);
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

### <a name="sample-output"></a>範例輸出

此輸出假設目前的目錄中只有一個檔案的副檔名為 .c。

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

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
