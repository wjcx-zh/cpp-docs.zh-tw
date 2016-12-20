---
title: "_getdrive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getdrive"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getdrive"
  - "getdrive"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getdrive 函式"
  - "目前的硬碟機"
  - "磁碟機"
  - "getdrive 函式"
ms.assetid: e40631a0-8f1a-4897-90ac-e1037ff30bca
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getdrive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得現用磁碟機。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _getdrive( void );  
```  
  
## 傳回值  
 傳回目前 \(預設\) 磁碟機 \(1\=A， 2\=B，依此類推\)。  不會回傳錯誤。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getdrive`|\<direct.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getdrive.c  
// compile with: /c  
// Illustrates drive functions including:  
//    _getdrive       _chdrive        _getdcwd  
//  
  
#include <stdio.h>  
#include <direct.h>  
#include <stdlib.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch, drive, curdrive;  
   static char path[_MAX_PATH];  
  
   // Save current drive.  
   curdrive = _getdrive();  
  
   printf( "Available drives are:\n" );  
  
   // If we can switch to the drive, it exists.  
   for( drive = 1; drive <= 26; drive++ )  
   {  
      if( !_chdrive( drive ) )  
      {  
         printf( "%c:", drive + 'A' - 1 );  
         if( _getdcwd( drive, path, _MAX_PATH ) != NULL )  
            printf( " (Current directory is %s)", path );  
         putchar( '\n' );  
      }  
   }  
  
   // Restore original drive.  
   _chdrive( curdrive );  
}  
```  
  
  **可用的磁碟機是:**  
**A: \(目前的目錄是 A:\\\)**  
**C: \(目前的目錄是 C:\\\)**  
**E:\(目前的目錄是 E:\\testdir\\bin\)**  
**F: \(目前的目錄是 F:\\\)**  
**G: \(目前的目錄是 G:\\\)**   
## .NET Framework 對等用法  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_chdrive](../../c-runtime-library/reference/chdrive.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdcwd、\_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)