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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 82a7e891e8bd6031ebbf761534b6df7cd8488d36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347380"
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

*Fd*<br/>
已開啟之檔案的檔案描述項。

*模式*<br/>
檔案存取的類型。

## <a name="return-value"></a>傳回值

這些函式中每一個都會傳回已開啟之資料流的指標。 null 指標值表示錯誤。 發生錯誤時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,errno**將設定為**EBADF**,指示錯誤的檔描述符, 或**EINVAL**, 指示*模式*是空指標。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_fdopen**函數將I/O流與*fd*識別的檔關聯,從而允許對為低級I/O打開的檔進行緩衝和格式化。 **_wfdopen**是 **_fdopen**的寬字元版本;_wfdopen*模式***_wfdopen**參數是寬字元字串。 **_wfdopen**和 **_fdopen**否則行為相同。

傳遞到 **_fdopen**的檔描述符由返回的**FILE &#42;** 流所有。 如果 **_fdopen**成功,請不要在檔案描述符[\_](close.md)上調使用 關閉 。 在返回的 FILE**上**調用[fclose&#42;](fclose-fcloseall.md)也會關閉檔描述符。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|\_未定義\_UNICODE 與 MBCS|\_MBCS 已定義|\_已定義 UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*模式*字串指定為檔案請求的檔案存取型態:

| *模式* | 存取 |
|--------|--------|
| **"r"** | 開啟以讀取。 如果檔案不存在或找不到,**則 fopen**呼叫將失敗。 |
| **"w"** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **"a"** | 打開以在檔末尾寫入(追加)。 如果檔案不存在時，建立檔案。 |
| **"r+"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w+"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a+"** | 開啟以進行讀取和附加。 如果檔案不存在時，建立檔案。 |

當使用 **"a"或"a+"** 存取 **"a+"** 類型打開檔時,所有寫入操作都發生在檔的末尾。 可以使用[fseek](fseek-fseeki64.md)或[後退](rewind.md)重新定位檔指標,但在執行任何寫入操作之前,該檔指標始終被移回檔末尾。因此,無法覆蓋現有數據。 指定 **"r+"、"w+"** 或 **"w+"****"a+"** 存取類型時,允許讀取和寫入(該檔表示為"更新"打開)。 但是,當您在閱讀和寫作之間切換時,必須有一個中間的 fflush、fsetpos、fseek 或[倒帶](rewind.md)操作。 [fflush](fflush.md) [fsetpos](fsetpos.md) [fseek](fseek-fseeki64.md) 如果需要,可以指定[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作的當前位置。

除上述值外,還可以在*模式下*包含以下字元,以指定換行元的轉換模式:

| *模式*修改器 | 行為 |
|-----------------|----------|
| **t** | 以文字 (已轉譯) 模式開啟。 在此模式中，會將歸位字元-換行字元 (CR-LF) 組合在輸入中轉譯成單行換行字元 (LF)，且會將 LF 字元在輸出中轉譯為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 |
| **B** | 以二進位 (未轉譯) 模式開啟。 禁止從**t**模式的任何轉換。 |
| **C** | 啟用關聯*檔名*的提交標誌,以便在調用**fflush**或 **_flushall**時,檔緩衝區的內容直接寫入磁碟。 |
| **n** | 將關聯*檔名*的提交標誌重置為"不提交」。 這是預設值。 如果將程式與 Commode.obj 連結,它還會覆蓋全域提交標誌。全域提交標誌預設值為「不提交」,除非您將程式與 Commode.obj 顯式連結。 |

**t、c**和**n** *模式*選項是 Microsoft 用於**c****fopen**和 **_fdopen**的擴展。 如果您想要保留 ANSI 可攜性，請勿使用它們。

如果在*模式下*未給出**t**或**b,** 則預設轉換模式由全域變數[\_fmode](../../c-runtime-library/fmode.md)定義。 如果**t**或**b**預固定到參數,則函數將失敗並傳回 NULL。 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

**fopen**與 **_fdopen**中使用的*型態*字串的字元對應[\_](open-wopen.md)於 open 與[\_sopen](sopen-wsopen.md)中使用的*滯後*參數,如下表所示:

|*模式*字串的字元|**_open**和 **_sopen**的*滯後*值等價值|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_ \_ \_WRONLY &#124; O APPEND(** 通常**\_O\_WRONLY &#124; \_ \_O CREAT &#124; \_O\_APPEND)**|
|**a+**|**\_O\_RDWR \_ \_&#124; O APPEND(** 通常**\_O\_RDWR &#124; \_ \_O APPEND &#124; \_O\_CREAT** )|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (通常**\_\_\_\_ \_O\_WRONLY &#124; O CREAT &#124; O TRUNC**)|
|**w***|**\_O\_RDWR** (通常**\_\_ \_ \_O \_\_RDWR &#124; O CREAT &#124; O TRUNC**)|
|**B**|**\_O\_BINARY**|
|**t**|**\_O\_文字**|
|**C**|None|
|**n**|None|

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
[\_欺騙,\_欺騙2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[開,wfopen \_](fopen-wfopen.md)<br/>
[弗賴恩\_,wf重新](freopen-wfreopen.md)<br/>
[\_開啟,\_開啟](open-wopen.md)<br/>
