---
title: _setmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setmode
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
- _setmode
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 23
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
ms.openlocfilehash: f6d84d5f40b49edaf4e79059a6661a51ca6c209a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="setmode"></a>_setmode
設定檔案轉譯模式。  
  
## <a name="syntax"></a>語法  
  
```  
int _setmode (  
   int fd,  
   int mode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `fd`  
 檔案描述項。  
  
 `mode`  
 新的轉譯模式。  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回之前的轉譯模式。  
  
 如果將無效參數傳遞至此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若要繼續，此函數會傳回-1 和設定允許執行`errno`為`EBADF`，表示無效的檔案描述項，或`EINVAL`，表示無效`mode`引數。  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_setmode` 函式會設定 `mode` 為 `fd` 所指定之檔案的轉譯模式。 若 `_O_TEXT` 設定文字 (亦即：已轉譯) 模式，則傳遞 `mode`。 歸位字元傳回行摘要 (CR-LF) 組合會轉譯成單行換上輸入的字元。 換行字元會在輸出中轉譯為 CR-LF 組合。 傳遞 `_O_BINARY` 可設定二進位 (未轉譯) 模式，此模式會抑止這些轉譯。  
  
 您也可以傳遞`_O_U16TEXT`， `_O_U8TEXT`，或`_O_WTEXT`啟用 Unicode 模式，如本文稍後的第二個範例所示。 一般而言會使用 `_setmode` 修改 `stdin` 和 `stdout` 的預設轉譯模式，但您可以將其用於任何檔案。 若您將 `_setmode` 套用於資料流的檔案描述項，請先呼叫 `_setmode`，再於資料流上執行任意輸入或輸出作業。  
  
> [!CAUTION]
>  如果您將資料寫入檔案資料流，請先使用 [fflush](../../c-runtime-library/reference/fflush.md) 明確地清除代碼，再使用 `_setmode` 變更模式。 若您沒有清除代碼，可能會發生未預期的行為。 若您沒有將資料寫入資料流，則不用清除代碼。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|----------------------|  
|`_setmode`|\<io.h>|\<fcntl.h>|  
  
 如需相容性詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_setmode.c  
// This program uses _setmode to change  
// stdin from text mode to binary mode.  
  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
int main( void )  
{  
   int result;  
  
   // Set "stdin" to have binary mode:  
   result = _setmode( _fileno( stdin ), _O_BINARY );  
   if( result == -1 )  
      perror( "Cannot set mode" );  
   else  
      printf( "'stdin' successfully changed to binary mode\n" );  
}  
```  
  
```Output  
'stdin' successfully changed to binary mode  
```  
  
## <a name="example"></a>範例  
  
```  
// crt_setmodeunicode.c  
// This program uses _setmode to change  
// stdout to Unicode. Cyrillic and Ideographic  
// characters will appear on the console (if  
// your console font supports those character sets).  
  
#include <fcntl.h>  
#include <io.h>  
#include <stdio.h>  
  
int main(void) {  
    _setmode(_fileno(stdout), _O_U16TEXT);  
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");  
    return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_set_fmode](../../c-runtime-library/reference/set-fmode.md)
