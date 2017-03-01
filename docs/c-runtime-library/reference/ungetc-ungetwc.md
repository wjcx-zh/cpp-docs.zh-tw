---
title: "ungetc、ungetwc | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 9f33416614f18a5a1cd7a61ccf4acfb9276de8e5
ms.lasthandoff: 02/24/2017

---
# <a name="ungetc-ungetwc"></a>ungetc、ungetwc
將字元推入回資料流。  
  
## <a name="syntax"></a>語法  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `c`  
 要推入的字元。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，所有這些函式都會傳回字元引數 `c`。 如果無法回推 `c` 或是未讀取任何字元，則輸入資料流不會變更，且 `ungetc` 會傳回 `EOF`；`ungetwc` 會傳回 `WEOF`。 如果 `stream` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回 `EOF` 或 `WEOF`，且 `errno` 會設定為 `EINVAL`。  
  
 如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `ungetc` 函式會將字元 `c` 推入至 `stream`，並清除檔案結尾指標。 資料流必須是開啟可供讀取。 對 `stream` 的後續讀取作業會從 `c` 開始。 會忽略嘗試使用 `ungetc` 將 `EOF` 推至資料流。  
  
 如果在從資料流讀取字元之前呼叫 `fflush`、`fseek`、`fsetpos` 或 `rewind`，`ungetc` 放在資料流的字元可能會被刪除。 檔案位置指標將具有在回推字元之前它所具有的值。 對應至資料流外部儲存體會保持不變。 在針對文字資料流的成功 `ungetc` 呼叫，將不會指定檔案位置指標，直到所有回推的字元都已讀取或捨棄為止。 在針對二進位資料流的每個成功 `ungetc` 呼叫，檔案位置指標會減少；如果其值在呼叫之前為 0，該值在呼叫之後為未定義。  
  
 如果呼叫 `ungetc` 兩次，而在兩次呼叫之間沒有讀取或檔案位置的作業，將無法預測結果。 在呼叫 `fscanf` 之後，呼叫 `ungetc` 可能會失敗，除非已執行另一個讀取作業 (例如 `getc`)。 這是因為 `fscanf` 本身會呼叫 `ungetc`。  
  
 `ungetwc` 是 `ungetc` 的寬字元版本。 不過，在針對文字或二進位資料流的每個成功 `ungetwc` 呼叫，將不會指定檔案位置指標，直到所有回推的字元都已讀取或捨棄為止。  
  
 這些函式是安全執行緒，並且會在執行期間鎖定機密資料。 如需非鎖定版本，請參閱 [_ungetc_nolock、_ungetwc_nolock](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`ungetc`|\<stdio.h>|  
|`ungetwc`|\<stdio.h> 或 \<wchar.h>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。 與主控台 (`stdin`、`stdout` 和 `stderr`) 關聯的標準資料流控制代碼必須重新導向，之後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
```Output  
  
      521aNumber = 521  
Next character in stream = 'a'  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)
