---
title: "_fgetchar、_fgetwchar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fgetchar
- _fgetwchar
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
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
dev_langs: C++
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b82613d11d2002c0236a720072826e66cb87d7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fgetchar-fgetwchar"></a>_fgetchar、_fgetwchar
從 `stdin` 讀取字元。  
  
## <a name="syntax"></a>語法  
  
```  
int _fgetchar( void );  
wint_t _fgetwchar( void );  
```  
  
## <a name="return-value"></a>傳回值  
 `_fgetchar` 會傳回已讀取為 `int` 的字元，或傳回 `EOF` 表示錯誤或檔案結尾。 **_**`fgetwchar` 會以 [wint_t](../../c-runtime-library/standard-types.md) 形式傳回對應至所讀取字元的寬字元，或傳回 `WEOF` 表示錯誤或檔案結尾。 針對這兩個函式，使用 `feof` 或 `ferror` 來區分錯誤與檔案結尾條件。  
  
## <a name="remarks"></a>備註  
 這些函式會從 `stdin` 讀取單一字元。 此函式接著會增加相關聯的檔案指標 (定義時) 以指向下一個字元。 如果資料流位於檔案結尾，則會設定資料流的檔案結尾指標。  
  
 `_fgetchar` 相當於 `fgetc( stdin )`。 它也相當於 `getchar`，但僅實作為函式，而不是函式和巨集。 `_fgetwchar` 是寬字元版本的 `_fgetchar`。  
  
 這些函式與 ANSI 標準不相容。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_fgettchar`|`_fgetchar`|`_fgetchar`|`_fgetwchar`|  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_fgetchar`|\<stdio.h>|  
|`_fgetwchar`|\<stdio.h> 或 \<wchar.h>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。 與主控台 (`stdin`、`stdout` 和 `stderr`) 關聯的標準資料流控制代碼必須重新導向，之後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_fgetchar.c  
// This program uses _fgetchar to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[81];  
   int  i, ch;  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = _fgetchar();  
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetchar();  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
}  
```  
  
```Output  
  
      Line one.  
Line two.Line one.  
Line two.  
```  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)