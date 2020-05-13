---
title: freopen、_wfreopen
ms.date: 4/2/2020
api_name:
- freopen
- _wfreopen
- _o__wfreopen
- _o_freopen
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
- _wfreopen
- _tfreopen
- freopen
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
ms.openlocfilehash: 435211b246f9943588aeef2005e501a9eac59c6b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916335"
---
# <a name="freopen-_wfreopen"></a>freopen、_wfreopen

重新指派檔案指標。 這些函式已有更安全的版本可用；請參閱 [freopen_s、_wfreopen_s](freopen-s-wfreopen-s.md)。

## <a name="syntax"></a>語法

```C
FILE *freopen(
   const char *path,
   const char *mode,
   FILE *stream
);
FILE *_wfreopen(
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*path*<br/>
新檔案的路徑。

*mode*<br/>
允許的存取類型。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回新開啟檔案的指標。 如果發生錯誤，則會關閉原始檔案，而函式會傳回**Null**指標值。 如果*path*、 *mode*或*stream*是 null 指標，或*filename*是空字串，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，並傳回**Null**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

這些函式已有更安全的版本，請參閱 [freopen_s、_wfreopen_s](freopen-s-wfreopen-s.md)。

**Freopen**函式會關閉目前與*stream*相關聯的檔案，並將*資料流程*重新指派至*path*所指定的檔案。 **_wfreopen**是寬字元版本的 **_freopen**;**_wfreopen**的*路徑*和*模式*引數是寬字元字串。 相反地， **_wfreopen**和 **_freopen**的行為相同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen**通常用來將預先開啟的檔案（ **stdin**、 **stdout**和**stderr** ）重新導向至使用者所指定的檔案。 與*stream*相關聯的新檔案會以*模式*開啟，這是一個字元字串，用來指定針對檔案所要求的存取類型，如下所示：

|*mode*|存取|
|-|-|
| **r** | 開啟以讀取。 如果檔案不存在或找不到， **freopen**呼叫將會失敗。 |
| **寬** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **為** | 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。 |
| **"r +"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w +"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a +"** | 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。 |

請小心使用 **"w"** 和 **"w +"** 類型，因為它們可以摧毀現有的檔案。

以 **"a"** 或 **"a +"** 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。 雖然可以使用[fseek](fseek-fseeki64.md) [或倒轉](rewind.md)來重新置放檔案指標，但是在執行任何寫入作業之前，檔案指標一律會移回至檔案結尾。因此，無法覆寫現有的資料。

在附加到檔案之前， **"a"** 模式不會移除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 **"A +"** 模式會先移除 EOF 標記，再將附加至檔案。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 附加至以 CTRL + Z EOF 標記終止的資料流程檔案時，需要 **"a +"** 模式。

指定 **"r +"**、 **"w +"** 或 **"a +"** 存取類型時，同時允許讀取和寫入（此檔案稱為「更新」）。 不過，當您在讀取和寫入之間切換時，必須有中間的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 作業。 如有需要，可以為[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)作業指定目前的位置。 除了上述的值，*模式*字串中可能會包含下列其中一個字元，以指定新行的轉譯模式。

|*模式*修飾詞|轉譯模式|
|-|-|
| **而已** | 以文字 (已轉譯) 模式開啟。 |
| **位元組** | 以二進位（未轉譯）模式開啟;會隱藏涉及回車和換行字元的翻譯。 |

在文字（已轉譯）模式中，在輸入時，會將換行字元（CR-LF）組合轉譯成單行換行字元（LF）在輸出時，LF 字元會轉譯成 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在開啟以供讀取的檔案，或使用 **"a +"** 進行寫入和讀取的檔案中，執行時間程式庫會在檔案結尾檢查是否有 CTRL + Z，並盡可能加以移除。 這是因為使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)在檔案內移動可能會使[fseek](fseek-fseeki64.md)在檔案結尾附近的行為不正確。 **T**選項是 Microsoft 擴充功能，不應在需要 ANSI 可攜性的情況下使用。

如果未在*模式*中指定**t**或**b** ，預設的轉譯模式會由全域變數[_fmode](../../c-runtime-library/fmode.md)定義。 如果**t**或**b**前面加上引數，則函式會失敗並傳回**Null**。

如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺（UWP）應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_freopen.c
// compile with: /W3
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.
#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   // Reassign "stderr" to "freopen.out":
   stream = freopen( "freopen.out", "w", stderr ); // C4996
   // Note: freopen is deprecated; consider using freopen_s instead

   if( stream == NULL )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
