---
title: freopen、_wfreopen
ms.date: 11/04/2016
apiname:
- freopen
- _wfreopen
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
ms.openlocfilehash: 4c570837bddea1f5e986ae5f767279ab2637ea21
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332500"
---
# <a name="freopen-wfreopen"></a>freopen、_wfreopen

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

所有這些函式都會傳回新開啟檔案的指標。 如果發生錯誤時，原始的檔案已關閉，且函式會傳回**NULL**指標值。 如果*路徑*，*模式*，或*串流*為 null 指標，或如果*filename*為空字串，這些函式叫用無效的參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**要**EINVAL** ，並傳回**NULL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

這些函式已有更安全的版本，請參閱 [freopen_s、_wfreopen_s](freopen-s-wfreopen-s.md)。

**Freopen**函式會關閉目前與相關聯的檔案*串流*並重試*串流*所指定的檔案*路徑*。 **_wfreopen**是寬字元版本的 **_freopen**;*路徑*並*模式*引數 **_wfreopen**是寬字元字串。 **_wfreopen**並 **_freopen**行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen**通常用來重新導向預先開啟的檔案**stdin**， **stdout**，和**stderr**使用者所指定的檔案。 新的檔案與相關聯*資料流*以開啟*模式*，這是字元字串，指定要求檔案，如下所示的存取類型：

|*mode*|存取|
|-|-|
| **"r"** | 開啟以讀取。 如果檔案不存在或無法找到**freopen**呼叫就會失敗。 |
| **"w"** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **"a"** | 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。 |
| **"r+"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w+"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a+"** | 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。 |

使用 **"w"** 並 **"w +"** 類型使用時請小心，因為它們可以終結現有的檔案。

與開啟檔案時 **"a"** 或是 **"a +"** 存取類型，所有寫入作業發生在檔案結尾。 雖然檔案指標可以使用定位[fseek](fseek-fseeki64.md)或是[倒轉](rewind.md)，檔案指標會永遠移回至檔案結尾之前執行任何寫入作業會。因此，無法覆寫現有資料。

**"A"** 模式不會附加到檔案之前移除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 **"A +"** 模式會附加到檔案之前移除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 **"A +"** 模式，才能附加至以 CTRL + Z EOF 標記終止的資料流檔案。

當 **"r +"**， **"w +"**，或 **"a +"** 指定存取類型，允許讀取和寫入 （檔案要開啟以供 「 更新 」）。 不過，當您在讀取和寫入之間切換時，必須有中間的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 作業。 可以指定目前的位置，如[fsetpos](fsetpos.md)或是[fseek](fseek-fseeki64.md)作業，如有需要。 除了上述的值，其中一個下列的字元可能會包含在*模式*字串，以指定新行的轉譯模式。

|*模式*修飾詞|轉譯模式|
|-|-|
| **t** | 以文字 (已轉譯) 模式開啟。 |
| **b** | 以二進位 (未轉譯) 模式開啟；抑制涉及歸位字元和換行字元的轉譯。 |

在文字 （已轉譯） 模式下，歸位字元傳回換行字元 (CR-LF) 組合會轉譯成單行換行字元 (LF) 字元上輸入;會將 LF 字元轉譯為 CR-LF 組合，在輸出上。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在 檔案開啟供讀取或寫入和讀取與 **"a +"**，執行階段程式庫會檢查是否有 CTRL + Z 結尾的檔案，並盡可能加以移除。 這是因為使用[fseek](fseek-fseeki64.md)並[ftell](ftell-ftelli64.md)為的檔案內移動可能會導致[fseek](fseek-fseeki64.md)檔案結尾附近產生不當行為。 **t**選項是 Microsoft 擴充功能，不應在需要 ANSI 可攜性。

如果**t**或是**b**中未指定*模式*，則預設轉譯模式由全域變數[_fmode](../../c-runtime-library/fmode.md)。 如果**t**或是**b**前面加上引數，函式會失敗並傳回**NULL**。

如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台中，相關聯的標準資料流控制代碼**stdin**， **stdout**，並**stderr**，必須重新導向，C 執行階段函式才能使用它們在 UWP 應用程式. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
[_fdopen、wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
