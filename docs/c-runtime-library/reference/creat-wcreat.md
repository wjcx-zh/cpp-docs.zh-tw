---
title: "_creat、_wcreat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _creat
- _wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
dev_langs: C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d8474031a7ba98952c258b4dc4041c7eff57c434
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creat-wcreat"></a>_creat、_wcreat
建立新檔案。 `_creat` 和 `_wcreat` 已被取代，請改用 [_sopen_s、_wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
int _creat(   
   const char *filename,  
   int pmode   
);  
int _wcreat(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 新檔案的名稱。  
  
 `pmode`  
 權限設定。  
  
## <a name="return-value"></a>傳回值  
 這些函式若成功，則傳回所建立檔案的檔案描述項。 否則，函式會傳回-1，並設定`errno`下表所示。  
  
|`errno` 設定|描述|  
|---------------------|-----------------|  
|`EACCES`|`filename` 會指定現有的唯讀檔案，或指定目錄而不是檔案。|  
|`EMFILE`|沒有更多檔案描述項可用。|  
|`ENOENT`|找不到指定的檔案。|  
  
 如果 `filename` 為 NULL，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` ，並傳回 -1。  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_creat` 函式會建立新的檔案，或開啟並截斷現有的檔案。 `_wcreat` 是寬字元版本的 `_creat`；`filename` 的 `_wcreat` 引數是寬字元字串。 否則，`_wcreat` 和 `_creat` 的行為即會相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcreat`|`_creat`|`_creat`|`_wcreat`|  
  
 如果 `filename` 所指定的檔案不存在，則會使用指定的權限設定建立新的檔案，然後開啟檔案以供寫入。 如果檔案已存在且其權限設定允許寫入，`_creat` 會將檔案長度截斷至 0 並終結先前的內容，然後開啟檔案以供寫入。 權限設定 `pmode` 只會套用至新建立的檔案。 新檔案會在第一次關閉之後收到指定的權限設定。 整數運算式 `pmode` 包含 SYS\Stat.h 中所定義的資訊清單常數 `_S_IWRITE` 及 (或) `_S_IREAD`。 指定兩個常數時，會使用位元 `OR` 運算子 (**&#124;**) 加以聯結。 `pmode` 參數會設定為下列其中一個值。  
  
|值|定義|  
|-----------|----------------|  
|`_S_IWRITE`|允許寫入|  
|`_S_IREAD`|允許讀取。|  
|`_S_IREAD &#124; _S_IWRITE`|允許讀取和寫入。|  
  
 若沒有指定寫入權限，則檔案為唯讀。 所有檔案皆為可讀取；不可能授與僅限寫入權限。 因此，模式 `_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 相同。 使用 `_creat` 開啟的檔案一律會在具有 `_SH_DENYNO` 的相容性模式中開啟 (請參閱 [_sopen](../../c-runtime-library/reference/sopen-wsopen.md))。  
  
 `_creat` 會在設定權限之前，將目前的檔案權限遮罩套用至 `pmode` (請參閱 [_umask](../../c-runtime-library/reference/umask.md))。 `_creat` 主要是為了與先前的程式庫相容所提供。 在 `oflag` 參數中使用 `_O_CREAT` 和 `_O_TRUNC` 呼叫 `_open` 相當於 `_creat`，並且適用於新的程式碼。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_creat`|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|  
|`_wcreat`|\<io.h> 或 \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_creat.c  
// compile with: /W3  
// This program uses _creat to create  
// the file (or truncate the existing file)  
// named data and open it for writing.  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int fh;  
  
   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996  
   // Note: _creat is deprecated; use _sopen_s instead  
   if( fh == -1 )  
      perror( "Couldn't create data file" );  
   else  
   {  
      printf( "Created data file.\n" );  
      _close( fh );  
   }  
}  
```  
  
```Output  
Created data file.  
```  
  
## <a name="see-also"></a>請參閱  
 [低層級 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_sopen、_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../../c-runtime-library/reference/umask.md)