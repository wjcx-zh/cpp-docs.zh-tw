---
title: "_fdopen、_wfdopen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
dev_langs: C++
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bacc1decd25c5c7291295a9e97eeacb35d55662c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="fdopen-wfdopen"></a>_fdopen、_wfdopen
將資料流與先前針對低層級 I/O 開啟的檔案建立關聯。  
  
## <a name="syntax"></a>語法  
  
```  
FILE *_fdopen(    
   int fd,  
   const char *mode   
);  
FILE *_wfdopen(   
   int fd,  
   const wchar_t *mode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `fd`  
 已開啟之檔案的檔案描述項。  
  
 `mode`  
 檔案存取的類型。  
  
## <a name="return-value"></a>傳回值  
 這些函式中每一個都會傳回已開啟之資料流的指標。 null 指標值表示錯誤。 發生錯誤時，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會將 `errno` 設為 `EBADF` (表示不正確的檔案描述項) 或 `EINVAL` (表示 `mode` 是 null 指標)。  
  
 如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_fdopen` 函式會將 I/O 資料流與 `fd` 所識別的檔案產生關聯，因此允許針對低層級 I/O 開啟的檔案經過緩衝處理和格式化。 `_wfdopen` 是寬字元版本的 `_fdopen`；`mode` 的 `_wfdopen` 引數是寬字元字串。 除此之外，`_wfdopen` 和 `_fdopen` 的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfdopen`|`_fdopen`|`_fdopen`|`_wfdopen`|  
  
 `mode` 字元字串會指定檔案和檔案存取的類型。  
  
 字元字串 `mode` 會指定對檔案要求的存取類型，如下表所示。  
  
 `"r"`  
 開啟以讀取。 如果檔案不存在或找不到， `fopen` 呼叫就會失敗。  
  
 `"w"`  
 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。  
  
 `"a"`  
 開啟以供在該檔案結尾寫入 (附加)。 如果檔案不存在時，建立檔案。  
  
 `"r+"`  
 開啟以進行讀取和寫入。 (檔案必須存在)。  
  
 `"w+"`  
 開啟空白檔案以進行讀取和寫入。 如果指定的檔案已存在，其內容將被終結。  
  
 `"a+"`  
 開啟以進行讀取和附加。 如果檔案不存在時，建立檔案。  
  
 使用 `"a"` 或 `"a+"` 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。 檔案指標可以使用 `fseek` 或 `rewind` 重新調整位置，但是在執行任何寫入作業之前，永遠會移回至檔案結尾。因此，無法覆寫現有資料。 指定 `"r+"`、`"w+"` 或 `"a+"` 存取類型時，同時允許讀取和寫入 (表示檔案是要開啟以供「更新」之用)。 不過，當您在讀取和寫入之間切換時，必須有中間的 `fflush`、`fsetpos`、`fseek` 或 `rewind` 作業。 您可以視需要指定 `fsetpos` 或 `fseek` 作業的目前位置。  
  
 除了上面的值之外，還可以將下列字元包含在 `mode`，指定新行字元的轉譯模式。  
  
 `t`  
 以文字 (已轉譯) 模式開啟。 在此模式中，會將歸位字元-換行字元 (CR-LF) 組合在輸入中轉譯成單行換行字元 (LF)，且會將 LF 字元在輸出中轉譯為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在為了讀取/寫入而開啟的檔案中，`fopen` 會盡可能檢查檔案結尾是否有 Ctrl+Z，並加以移除。 之所以這樣做，是因為使用 `fseek` 和 `ftell` 函式在以 Ctrl+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不正確的行為。  
  
 `b`  
 以二進位 (未轉譯) 模式開啟。 會隱藏任何來自 `t` 模式的轉譯。  
  
 `c`  
 啟用關聯 `filename` 的認可旗標，以便在呼叫 `fflush` 或 `_flushall` 時，將檔案緩衝區的內容直接寫入磁碟。  
  
 `n`  
 將關聯 `filename` 的認可旗標重設為 "no-commit"。 這是預設值。 如果將程式與 Commode.obj 連結，也會覆寫全域認可旗標。除非您明確將程式與 Commode.obj 連結，否則全域認可旗標預設值為 "no-commit"。  
  
 `t`、`c` 和 `n` `mode` 選項是 `fopen` 和 `_fdopen` 的 Microsoft 延伸模組。 如果您想要保留 ANSI 可攜性，請勿使用它們。  
  
 如果 `mode` 中未指定 `t` 或 `b`，則預設轉譯模式由全域變數 [_fmode](../../c-runtime-library/fmode.md) 定義。 如果引數前置 `t` 或 `b` ，則函式失敗並傳回 `NULL`。 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
 `fopen` 和 `_fdopen` 中所用之 `mode` 字串的有效字元會對應用於 [_open](../../c-runtime-library/reference/open-wopen.md) 和 [_sopen](../../c-runtime-library/reference/sopen-wsopen.md) 的 `oflag` 引數，如下所示。  
  
|`mode` 字串中的字元|`_open`/`_sopen` 的對等 `oflag` 值|  
|---------------------------------|---------------------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND`(通常為 `_O_WRONLY &#124; _O_CREAT &#124; _O_APPEND`)|  
|`a+`|`_O_RDWR &#124; _O_APPEND` (通常為 `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT` )|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY` (通常為 `_O_WRONLY &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`w+`|`_O_RDWR` (通常為 `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`b`|`_O_BINARY`|  
|`t`|`_O_TEXT`|  
|`c`|無|  
|`n`|無|  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`_fdopen`|\<stdio.h>|  
|`_wfdopen`|\<stdio.h> 或 \<wchar.h>|  
  
 如需相容性詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="input-crtfdopentxt"></a>輸入：crt_fdopen.txt  
  
```  
Line one  
Line two  
```  
  
### <a name="output"></a>輸出  
  
```  
Lines in file: 2  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)