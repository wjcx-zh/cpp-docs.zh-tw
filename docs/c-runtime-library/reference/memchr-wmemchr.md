---
title: "memchr、wmemchr | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wmemchr"
  - "memchr"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "memchr"
  - "wmemchr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "memchr 函式"
  - "wmemchr 函式"
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# memchr、wmemchr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找在緩衝區的字元。  
  
## 語法  
  
```  
void *memchr(  
   const void *buf,  
   int c,  
   size_t count  
); // C only  
void *memchr(  
   void *buf,  
   int c,  
   size_t count  
); // C++ only  
const void *memchr(  
   const void *buf,  
   int c,  
   size_t count  
); // C++ only  
wchar_t *wmemchr(  
   const wchar_t * buf,   
   wchar_t c,  
   size_t count  
); // C only  
wchar_t *wmemchr(  
   wchar_t * buf,   
   wchar_t c,  
   size_t count  
); // C++ only  
const wchar_t *wmemchr(  
   const wchar_t * buf,   
   wchar_t c,  
   size_t count  
); // C++ only  
```  
  
#### 參數  
 `buf`  
 緩衝區的指標。  
  
 `c`  
 要尋找的字元。  
  
 `count`  
 要檢查的字元數。  
  
## 傳回值  
 如果成功的話，會傳回指標至`buf`中`c` 的第一個位置。  否則，會傳回 `NULL`。  
  
## 備註  
 `memchr` 和`wmemchr`尋找`c`在`buf`中第一個`count`位元組的第一次出現。  當他找到`c`或是檢查到第一個`count`位元組時，他會停止。  
  
 在 C 裏，這些函式的第一個引數採用 `const` 的指標。  在 C\+\+ 裏，有兩個多載版本可供使用。  多載的一個版本接受 `const` 的指標並回傳 `const` 的指標。另一個則接受 `const` 的指標並回傳非 `const` 的指標。  如果 `const` 和非 `const` 的版本均可用，會定義巨集 \_CONST\_CORRECT\_OVERLOADS 。  如果您需要 C\+\+ 兩個overloadsin C\+\+版本有非 `const` 的行為，請定義符號 \_CONST\_RETURN 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`memchr`|\<memory.h\> 或 \<string.h\>|  
|`wmemchr`|\<wchar.h\>|  
  
 如需更多相容性的資訊，請參閱 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_memchr.c  
  
#include <memory.h>  
#include <stdio.h>  
  
int  ch = 'r';  
char str[] =    "lazy";  
char string[] = "The quick brown dog jumps over the lazy fox";  
char fmt1[] =   "         1         2         3         4         5";  
char fmt2[] =   "12345678901234567890123456789012345678901234567890";  
  
int main( void )  
{  
   char *pdest;  
   int result;  
   printf( "String to be searched:\n             %s\n", string );  
   printf( "             %s\n             %s\n\n", fmt1, fmt2 );  
  
   printf( "Search char: %c\n", ch );  
   pdest = memchr( string, ch, sizeof( string ) );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf( "Result:      %c found at position %d\n", ch, result );  
   else  
      printf( "Result:      %c not found\n" );  
}  
```  
  
## Output  
  
```  
String to be searched:  
             The quick brown dog jumps over the lazy fox  
                      1         2         3         4         5  
             12345678901234567890123456789012345678901234567890  
  
Search char: r  
Result:      r found at position 12  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strchr、wcschr、\_mbschr、\_mbschr\_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)