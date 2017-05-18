---
title: "freopen、_wfreopen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 47b45dd9e2ad07032529652021172ea64b84d652
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="freopen-wfreopen"></a>freopen、_wfreopen
重新指派檔案指標。 這些函式已有更安全的版本可用；請參閱 [freopen_s、_wfreopen_s](../../c-runtime-library/reference/freopen-s-wfreopen-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `path`  
 新檔案的路徑。  
  
 `mode`  
 允許的存取類型。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 所有這些函式都會傳回新開啟檔案的指標。 如果發生錯誤，就會關閉原始檔案，而且函式會傳回 `NULL` 指標值。 如果 `path`、`mode` 或 `stream` 為 Null 指標，或 `filename` 為空字串，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `NULL`。  
  
 如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 這些函式已有更安全的版本，請參閱 [freopen_s、_wfreopen_s](../../c-runtime-library/reference/freopen-s-wfreopen-s.md)。  
  
 `freopen`函式會關閉目前與相關聯的檔案`stream`並重試`stream`所指定的檔案`path`。 `_wfreopen` 是 `_freopen` 的寬字元版本；`_wfreopen` 的 `path` 和 `mode` 引數是寬字元字串。 否則，`_wfreopen` 和 `_freopen` 的行為即會相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen`|`freopen`|`freopen`|`_wfreopen`|  
  
 `freopen` 通常用來將已預先開啟的檔案 `stdin`、`stdout` 和 `stderr` 導向至使用者所指定的檔案。 新的檔案與相關聯`stream`開啟`mode`，這是字元字串，指定對檔案要求的如下所示的存取類型︰  
  
 `"r"`  
 開啟以讀取。 如果檔案不存在或找不到， `freopen` 呼叫就會失敗。  
  
 `"w"`  
 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。  
  
 `"a"`  
 開啟以供在檔案結尾寫入 (附加)，並且在新資料寫入檔案之前，不會移除 EOF 標記；如果該檔案不存在，便會先建立檔案。  
  
 `"r+"`  
 開啟以進行讀取和寫入。 (檔案必須存在)。  
  
 `"w+"`  
 開啟空白檔案以進行讀取和寫入。 如果指定的檔案已存在，其內容將被終結。  
  
 `"a+"`  
 開啟以進行讀取和附加；此附加作業包含在將新資料寫入檔案之前移除 EOF 標記，且寫入完成後會復原 EOF 標記；如果該檔案不存在，便會先建立檔案。  
  
 請小心使用 `"w"` 和 `"w+"` 類型，因為它們可以終結現有的檔案。  
  
 使用 `"a"` 或 `"a+"` 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。 雖然檔案指標可以使用 `fseek` 或 `rewind` 重新調整位置，但是在執行任何寫入作業之前，一律會將此檔案指標移回至檔案結尾。 因此，無法覆寫現有資料。  
  
 在附加到檔案之前，`"a"` 模式不會移除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 在附加到檔案之前，`"a+"` 模式會移除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 附加至以 CTRL+Z EOF 標記終止的資料流檔案時，需要 `"a+"` 模式。  
  
 指定 `"r+"`、`"w+"` 或 `"a+"` 存取類型時，同時允許讀取和寫入 (表示檔案是要開啟以供「更新」之用)。 不過，當您在讀取和寫入之間切換時，必須有中間的 [fsetpos](../../c-runtime-library/reference/fsetpos.md)、[fseek](../../c-runtime-library/reference/fseek-fseeki64.md) 或 [rewind](../../c-runtime-library/reference/rewind.md) 作業。 如有需要，可以針對 `fsetpos` 或 `fseek` 作業指定目前位置。 除了上面的值之外，可以將下列字元包含在 `mode` 字串中以指定新行的轉譯模式。  
  
 `t`  
 以文字 （已轉譯） 模式開啟。歸位字元傳回換行字元 (CR-LF) 組合中轉譯成單行換行字元 (LF) 字元上輸入，會將 LF 字元轉譯為 CR-LF 組合輸出上。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在為了讀取或以 `"a+"` 讀取和寫入而開啟的檔案中，該執行階段程式庫會盡可能檢查檔案結尾是否有 Ctrl+Z，並加以移除。 之所以這樣做，是因為使用 `fseek` 和 `ftell` 在檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不當行為。 `t` 選項是 Microsoft 擴充功能，不應在需要 ANSI 可攜性的情況中使用。  
  
 `b`  
 在二進位 (未轉譯) 模式中開啟；會隱藏上述轉譯。  
  
 如果 `mode` 中未指定 `t` 或 `b`，則預設轉譯模式是透過全域變數 [_fmode](../../c-runtime-library/fmode.md) 所定義。 如果引數前置 `t` 或 `b` ，則函式失敗並傳回 `NULL`。  
  
 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`freopen`|\<stdio.h>|  
|`_wfreopen`|\<stdio.h> 或 \<wchar.h>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。 與主控台 (`stdin`、`stdout` 和 `stderr`) 關聯的標準資料流控制代碼必須重新導向，之後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen、_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)
