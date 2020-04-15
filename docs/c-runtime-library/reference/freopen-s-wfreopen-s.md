---
title: freopen_s、_wfreopen_s
ms.date: 4/2/2020
api_name:
- _wfreopen_s
- freopen_s
- _o__wfreopen_s
- _o_freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
ms.openlocfilehash: a24e34ead905d2f704bfbf4d829064c656272e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345923"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s、_wfreopen_s

重新指派檔案指標。 這些版本的 [freopen、_wfreopen](freopen-wfreopen.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*pFile*<br/>
指向要由此呼叫提供的檔案指標之指標。

*路徑*<br/>
新檔案的路徑。

*模式*<br/>
允許的存取類型。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

每一此函式都會傳回錯誤碼。 如果發生錯誤，就會關閉原始的檔案。

## <a name="remarks"></a>備註

**freopen_s**函數關閉當前與*流*關聯的檔,並將*流*重新分配給*路徑*指定的檔。 **_wfreopen_s**是 **_freopen_s**的寬字元版本;**_wfreopen_s的***路徑*和*模式*參數是寬字元字串。 **_wfreopen_s**和 **_freopen_s**行為相同。

如果任何*pFile、**路徑*、*模式*或*串*流為**NULL,** 或者如果*路徑*是空字串,則這些函數將呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將**errno**設定為**EINVAL**並傳回**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s**通常用於將預先打開的檔**stdin、std****和** **stder**重定向到使用者指定的檔。 與*串*流關聯的新檔案將開啟 mode ,該*模式*是指定檔案請求的存取類型的字串,如下所示:

|*模式*|存取|
|-|-|
| **"r"** | 開啟以讀取。 如果檔案不存在或找不到,**則freopen_s**呼叫失敗。 |
| **"w"** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **"a"** | 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。 |
| **"r+"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w+"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a+"** | 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。 |

小心使用 **"w"** 和 **"w+"** 類型,因為它們可以銷毀現有檔。

當使用 **"a"或"a+"** 存取 **"a+"** 類型打開檔時,所有寫入操作都發生在檔的末尾。 儘管可以使用[fseek](fseek-fseeki64.md)或[後退](rewind.md)重新定位檔指標,但檔指標始終在進行任何寫入操作之前移回檔末尾。因此,無法覆蓋現有數據。

在追加到檔案之前 **,"a"** 模式不會刪除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 **"a+"** 模式在追加到檔之前確實會刪除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 **"a+"** 模式是追加到使用 CTRL_Z EOF 標記終止的流檔所必需的。

指定 **"r+"、"w+"** 或 **"w+"****"a+"** 存取類型時,允許讀取和寫入(該檔表示為"更新"打開)。 不過，當您在讀取和寫入之間切換時，必須有中間的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 作業。 如果需要,可以為[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作指定當前位置。 除了上述值外,*模式*字串中可能包含以下字元之一,以指定新行的轉換模式。

|*模式*修改器|翻譯模式|
|-|-|
| **t** | 以文字 (已轉譯) 模式開啟。 |
| **B** | 在二進位(未翻譯)模式下打開;禁止使用涉及回車符和換行符的翻譯。 |

在文字(翻譯)模式下,車廂返回行饋送 (CR-LF) 組合在輸入時轉換為單行饋送 (LF) 字元;LF 字元在輸出時轉換為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在打開用於讀取或使用 **「a+」** 進行寫入和讀取的檔中,執行時庫會檢查檔末尾的 CTRL_Z 並刪除它(如果可能)。 這樣做是因為使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)在檔內移動可能會導致[fseek](fseek-fseeki64.md)在檔末尾附近行為不當。 **t**選項是 Microsoft 擴展,在需要 ANSI 可移植性的情況下不應使用。

如果在*模式下*未給出**t**或**b,** 則預設轉換模式由全域變數[_fmode](../../c-runtime-library/fmode.md)定義。 如果**t**或**b**預置到參數,則函數會失敗並傳回**NULL**。

如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺 (UWP) 應用中不支援該主控台。 在與主控台 **、stdin、stdout**和**stder**關聯的標準流句柄必須重定向,C 運行時函數才能在UWP應用中使用**stdout**它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
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
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
