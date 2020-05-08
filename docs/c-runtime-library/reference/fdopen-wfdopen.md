---
title: _fdopen、_wfdopen
ms.date: 4/2/2020
api_name:
- _fdopen
- _wfdopen
- _o__fdopen
- _o__wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 227f9e31c689b0259c429e2ffd9fce074903bd71
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920182"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen、_wfdopen

將資料流與先前針對低層級 I/O 開啟的檔案建立關聯。

## <a name="syntax"></a>語法

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>參數

*fd*<br/>
已開啟之檔案的檔案描述項。

*mode*<br/>
檔案存取的類型。

## <a name="return-value"></a>傳回值

這些函式中每一個都會傳回已開啟之資料流的指標。 null 指標值表示錯誤。 發生錯誤時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設定為**EBADF**，這表示不正確的檔案描述項，或**EINVAL**，表示該*模式*為 null 指標。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Fdopen**函式會將 i/o 資料流程與*fd*所識別的檔案產生關聯，因此可讓針對低層級 i/o 開啟的檔案進行緩衝處理和格式化。 **_wfdopen**是寬字元版本的 **_fdopen**;**_wfdopen**的*模式*引數是寬字元字串。 **_wfdopen**和 **_fdopen**的行為也相同。

傳遞至 **_fdopen**的檔案描述項是由傳回的檔案 **&#42;** 資料流程所擁有。 如果 **_fdopen**成功，請勿在檔案描述項上呼叫[ \_close](close.md) 。 在傳回的檔案上呼叫[fclose](fclose-fcloseall.md) **&#42;** 也會關閉檔案描述項。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|\_未定義\_UNICODE 和 MBCS|\_定義的 MBCS|\_已定義 UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*模式*字元字串會指定對檔案要求的檔存取類型：

| *mode* | 存取 |
|--------|--------|
| **r** | 開啟以讀取。 如果檔案不存在或找不到， **fopen**呼叫將會失敗。 |
| **寬** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **為** | 開啟以供在檔案結尾寫入（附加）。 如果檔案不存在時，建立檔案。 |
| **"r +"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w +"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a +"** | 開啟以進行讀取和附加。 如果檔案不存在時，建立檔案。 |

以 **"a"** 或 **"a +"** 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。 您可以使用[fseek](fseek-fseeki64.md) [或倒轉](rewind.md)來重新置放檔案指標，但是在執行任何寫入作業之前，一律會移回至檔案結尾。因此，無法覆寫現有的資料。 指定 **"r +"**、 **"w +"** 或 **"a +"** 存取類型時，同時允許讀取和寫入（此檔案稱為「更新」）。 不過，當您在讀取和寫入之間切換時，必須有中間的[fflush](fflush.md)、 [fsetpos](fsetpos.md)、 [fseek](fseek-fseeki64.md)或[倒轉](rewind.md)作業。 如有需要，您可以指定[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)作業的目前位置。

除了上述的值之外，下列字元也可以包含在*模式*中，以指定分行符號的轉譯模式：

| *模式*修飾詞 | 行為 |
|-----------------|----------|
| **而已** | 以文字 (已轉譯) 模式開啟。 在此模式中，會將歸位字元-換行字元 (CR-LF) 組合在輸入中轉譯成單行換行字元 (LF)，且會將 LF 字元在輸出中轉譯為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 |
| **位元組** | 以二進位 (未轉譯) 模式開啟。 禁止任何來自**t**模式的翻譯。 |
| **c** | 啟用相關聯*檔案名*的認可旗標，以便在呼叫**fflush**或 **_flushall**時，將檔案緩衝區的內容直接寫入磁片。 |
| **n** | 將相關聯*檔案名*的認可旗標重設為「未認可」。 這是預設值。 如果您將程式與 Commode.obj 連結，它也會覆寫全域認可旗標。除非您明確地將程式與 Commode.obj 連結，否則全域認可旗標預設值為「無認可」。 |

[ **T**]、[ **c**] 和 [ **n** *] 模式*選項是適用于**fopen**和 **_fdopen**的 Microsoft 擴充功能。 如果您想要保留 ANSI 可攜性，請勿使用它們。

如果未在*模式*中指定**t**或**b** ，則預設轉譯模式是由全域變數[ \_fmode](../../c-runtime-library/fmode.md)所定義。 如果**t**或**b**前面加上引數，則函式會失敗並傳回 Null。 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

**Fopen**和 **_fdopen**中使用之*模式*字串的有效字元，會對應到在[ \_open](open-wopen.md)和[ \_sopen](sopen-wsopen.md)中使用的*oflag*引數，如下表所示：

|*模式*字串中的字元|**_Open**和 **_sopen**的對等*oflag*值|
|---------------------------------|---------------------------------------------------|
|**為**|**\_O\_WRONLY &#124; \_o\_附加**（通常** \_是\_o WRONLY \_&#124;\_o 會\_&#124;\_o append**）|
|**a +**|**\_O\_RDWR &#124; \_o\_附加**（通常** \_是\_O RDWR \_&#124;\_o 附加\_&#124;\_o** ）|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** （通常** \_是\_o WRONLY \_&#124;\_o 會\_&#124;\_o TRUNC**）|
|**w +**|**\_O\_RDWR** （通常** \_是\_o RDWR \_&#124;\_o 會\_&#124;\_o TRUNC**）|
|**位元組**|**\_O\_二進位**|
|**而已**|**\_O\_文字**|
|**c**|無|
|**n**|無|

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>輸入：crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>輸出

```Output
Lines in file: 2
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup、 \_dup2](dup-dup2.md)<br/>
[fclose、 \_fcloseall](fclose-fcloseall.md)<br/>
[fopen、 \_wfopen](fopen-wfopen.md)<br/>
[freopen、 \_wfreopen](freopen-wfreopen.md)<br/>
[\_open、 \_wopen](open-wopen.md)<br/>
