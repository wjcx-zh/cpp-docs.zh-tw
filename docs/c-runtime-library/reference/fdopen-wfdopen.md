---
title: _fdopen、_wfdopen
ms.date: 12/12/2017
apiname:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: c68bc835adf19df7f1538d30b2be162fe6dc6021
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584453"
---
# <a name="fdopen-wfdopen"></a>_fdopen、_wfdopen

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

這些函式中每一個都會傳回已開啟之資料流的指標。 null 指標值表示錯誤。 發生錯誤時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續，請執行**errno**設為**EBADF**，表示不正確的檔案描述項，或**EINVAL**，這表示*模式*是 null 指標。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Fdopen**函式會將 I/O 資料流關聯的檔案，由*fd*，因此允許緩衝處理和格式化的低層級 I/O 開啟的檔案。 **_wfdopen**是寬字元版本的 **_fdopen**;*模式*引數 **_wfdopen**是寬字元字串。 **_wfdopen**並 **_fdopen**否則運作方式完全相同。

檔案描述元傳遞至 **_fdopen**擁有由傳回**檔案&#42;** 資料流。 如果 **_fdopen**成功時，不會呼叫[\_關閉](close.md)上的檔案描述項。 呼叫[fclose](fclose-fcloseall.md)針對傳回**檔案&#42;** 也會關閉檔案描述元。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|\_UNICODE 和\_MBCS 未定義|\_定義 MBCS|\_定義的 UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*模式*字元字串會指定對檔案要求的檔案存取類型：

|*mode*|存取|
|-|-|
**"r"**|開啟以讀取。 如果檔案不存在或無法找到**fopen**呼叫就會失敗。
**"w"**|開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。
**"a"**|開啟以供寫入 （附加） 的檔案結尾。 如果檔案不存在時，建立檔案。
**"r+"**|開啟以進行讀取和寫入。 檔案必須存在。
**"w+"**|開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。
**"a+"**|開啟以進行讀取和附加。 如果檔案不存在時，建立檔案。

與開啟檔案時 **"a"** 或是 **"a +"** 存取類型，所有寫入作業都會在檔案結尾。 檔案指標可以使用重新定位到[fseek](fseek-fseeki64.md)或是[倒轉](rewind.md)，但它會永遠移回至檔案結尾之前的作業會執行任何寫入。因此，無法覆寫現有資料。 當 **"r +"**， **"w +"**，或 **"a +"** 指定存取類型，允許讀取和寫入 （檔案要開啟以供 「 更新 」）。 不過，當您讀取和寫入之間切換時，必須有中間[fflush](fflush.md)， [fsetpos](fsetpos.md)， [fseek](fseek-fseeki64.md)，或[倒轉](rewind.md)作業。 您可以指定目前的位置，如[fsetpos](fsetpos.md)或是[fseek](fseek-fseeki64.md)作業，如果您想要。

除了上述的值，將下列字元可以也包含在*模式*來指定新行字元的轉譯模式：

|*模式*修飾詞|行為|
|-|-|
**t**|以文字 (已轉譯) 模式開啟。 在此模式中，會將歸位字元-換行字元 (CR-LF) 組合在輸入中轉譯成單行換行字元 (LF)，且會將 LF 字元在輸出中轉譯為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。
**b**|以二進位 (未轉譯) 模式開啟。 從任何翻譯**t**模式會隱藏。
**C**|啟用相關聯的認可旗標*檔名*使檔案緩衝區的內容會直接寫入磁碟**fflush**或是 **_flushall**呼叫。
**n**|重設相關聯的認可旗標*filename*以 「 不認可 」。 這是預設值。 如果將程式與 Commode.obj 連結，也會覆寫全域認可旗標。除非您明確將程式與 Commode.obj 連結，否則全域認可旗標預設值為 "no-commit"。

**t**， **c**，並**n** *模式*選項都是 Microsoft 擴充功能**fopen**及 **_fdopen**。 如果您想要保留 ANSI 可攜性，請勿使用它們。

如果**t**或是**b**中未指定*模式*，則預設轉譯模式由全域變數[ \_fmode](../../c-runtime-library/fmode.md)。 如果**t**或是**b**前面加上引數，則函式會失敗並傳回 NULL。 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

有效字元*模式*中所使用的字串**fopen**並 **_fdopen**對應至*oflag*引數中使用[\_開啟](open-wopen.md)並[ \_sopen](sopen-wsopen.md)，如本表所示：

|中的字元*模式*字串|對等*oflag*值 **_open**和 **_sopen**|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY &#124; \_O\_附加**(通常 **\_O\_WRONLY &#124; \_O\_建立&#124; \_O\_APPEND**)|
|**+**|**\_O\_RDWR &#124; \_O\_附加**(通常 **\_O\_RDWR &#124; \_O\_新增&#124; \_O\_建立**)|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (通常 **\_O\_WRONLY &#124; \_O\_建立&#124; \_O\_TRUNC**)|
|**w +**|**\_O\_RDWR** (通常 **\_O\_RDWR &#124; \_O\_建立&#124; \_O\_TRUNC**)|
|**b**|**\_O\_BINARY**|
|**t**|**\_O\_TEXT**|
|**C**|無|
|**n**|無|

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

### <a name="input-crtfdopentxt"></a>輸入：crt_fdopen.txt

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
[\_dup， \_dup2](dup-dup2.md)<br/>
[fclose、 \_fcloseall](fclose-fcloseall.md)<br/>
[fopen、 \_wfopen](fopen-wfopen.md)<br/>
[freopen、 \_wfreopen](freopen-wfreopen.md)<br/>
[\_開啟， \_wopen](open-wopen.md)<br/>
