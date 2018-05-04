---
title: freopen_s、_wfreopen_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfreopen_s
- freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
dev_langs:
- C++
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04b136a46672838fd6ee554668353d92796abc7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="freopens-wfreopens"></a>freopen_s、_wfreopen_s

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

*path*<br/>
新檔案的路徑。

*mode*<br/>
允許的存取類型。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

每一此函式都會傳回錯誤碼。 如果發生錯誤，就會關閉原始的檔案。

## <a name="remarks"></a>備註

**Freopen_s**函式會關閉目前與相關聯的檔案*資料流*並重試*資料流*所指定的檔案*路徑*. **_wfreopen_s**是寬字元版本的 **_freopen_s**;*路徑*和*模式*引數 **_wfreopen_s**是寬字元字串。 **_wfreopen_s**和 **_freopen_s**除此之外的行為相同。

如果任何一個*pFile*，*路徑*，*模式*，或*資料流*是**NULL**，或如果*路徑*為空字串，這些函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s**通常用來重新導向預先開啟的檔案**stdin**， **stdout**，和**stderr**使用者所指定的檔案。 新的檔案與相關聯*資料流*開啟*模式*，這是字元字串，指定對檔案要求的如下所示的存取類型：

|*mode*|存取|
|-|-|
**"r"**|開啟以讀取。 如果檔案不存在或找不到**freopen_s**呼叫就會失敗。
**"w"**|開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。
**"a"**|開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。
**"r+"**|開啟以進行讀取和寫入。 檔案必須存在。
**"w+"**|開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。
**"a+"**|開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。

使用 **"w"** 和 **"w +"** 類型時請務必小心，因為它們可以終結現有的檔案。

當開啟檔案時，與 **"a"** 或 **"+"** 存取類型，所有寫入作業發生在檔案結尾處。 雖然檔案指標可以使用定位[fseek](fseek-fseeki64.md)或[倒轉](rewind.md)，檔案指標會一律移回至檔案結尾之前任何寫入作業會執行。因此，無法覆寫現有資料。

**"A"** 模式不會附加到檔案之前移除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 **"+"** 模式會附加到檔案之前移除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 **"+"** 模式是需要附加至以 CTRL + Z EOF 標記終止的資料流檔案。

當 **"r +"**， **"w +"**，或 **"+"** 指定存取型別，允許進行讀取和寫入 （檔案要開啟以供 「 更新 」）。 不過，當您在讀取和寫入之間切換時，必須有中間的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md) 或 [rewind](rewind.md) 作業。 可以針對指定的目前位置[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)作業，如有需要。 除了上述的值，下列字元的其中一個可能包含在*模式*字串，指定新行的轉譯模式。

|*模式*修飾詞|轉譯模式|
|-|-|
**t**|以文字 (已轉譯) 模式開啟。
**b**|以二進位 (未轉譯) 模式開啟；抑制涉及歸位字元和換行字元的轉譯。

在文字 （轉譯） 模式下，歸位字元傳回換行字元 (CR-LF) 組合會轉譯成單行換行字元 (LF) 字元上輸入，會將 LF 字元轉譯為 CR-LF 組合輸出上。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在以讀取和寫入而開啟的讀取或檔案 **"+"**，執行階段程式庫會檢查是否有 CTRL + Z，檔案的結尾，並盡可能加以移除。 這是因為使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)為的檔案內移動可能會導致[fseek](fseek-fseeki64.md)檔案結尾附近產生不當行為。 **t**選項是 Microsoft 擴充功能，不應在需要 ANSI 可攜性。

如果**t**或**b**中未指定*模式*，則預設轉譯模式由全域變數[_fmode](../../c-runtime-library/fmode.md)。 如果**t**或**b**前置引數，函式失敗並傳回**NULL**。

如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 在主控台中，與相關聯的標準資料流控制代碼**stdin**， **stdout**，和**stderr**，必須重新導向之後 C 執行階段函式可以在 UWP 應用程式中使用它們,. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
f[reopen、_wfreopen](freopen-wfreopen.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
