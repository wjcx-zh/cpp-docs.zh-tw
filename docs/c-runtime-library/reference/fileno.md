---
title: "_fileno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fileno"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_fileno"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案控制代碼 [C++], 從資料流取得"
  - "fileno 函式"
  - "_fileno 函式"
  - "資料流, 取得檔案控制代碼"
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _fileno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得與資料流作關聯的檔案描述項。  
  
## 語法  
  
```  
int _fileno(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 `FILE` 結構的指標。  
  
## 傳回值  
 `_fileno` 傳回的檔案描述項。  不會回傳錯誤。  如果 `stream` 沒有指定開啟檔案，則結果會是未定義。  如果資料流為 `NULL`，\_`fileno` 則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `errno`，並將 `EINVAL` 設為 \-1。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
> [!NOTE]
>  如果 `stdout` 或 `stderr` 沒有相關聯的輸出資料流 \(例如，在沒有主控台視窗的 Windows 應用程式\)，傳回的檔案描述項為 \-2。  在舊版本中，傳回的檔案描述項為 \-1。  這項變更可以讓應用程式與錯誤區別此情況。  
  
## 備註  
 `_fileno` 方法會傳回檔案描述目前與 `stream`。  這個常式會實作為函式和當做巨集。  如需選擇實作的詳細資訊，請參閱 [選取函式和巨集之間](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) 。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fileno`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_fileno.c  
// This program uses _fileno to obtain  
// the file descriptor for some standard C streams.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );  
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );  
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );  
}  
```  
  
  **stdin 的檔案描述項為 0**  
**將 stdout 的檔案描述項為 1**  
**將 stderr 的檔案描述項為 2**   
## .NET Framework 對等用法  
 [System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [\_filelength、\_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)