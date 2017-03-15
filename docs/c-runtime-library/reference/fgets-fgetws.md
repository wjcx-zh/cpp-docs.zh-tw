---
title: "fgets、fgetws | Microsoft Docs"
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
  - "fgets"
  - "fgetws"
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
  - "_fgetts"
  - "fgetws"
  - "fgets"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgetts 函式"
  - "fgets 函式"
  - "fgetts 函式"
  - "fgetws 函式"
  - "資料流, 取得字串來源"
  - "資料流, 讀取自"
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgets、fgetws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料流會取得字串。  
  
## 語法  
  
```  
char *fgets(   
   char *str,  
   int n,  
   FILE *stream   
);  
wchar_t *fgetws(   
   wchar_t *str,  
   int n,  
   FILE *stream   
);  
```  
  
#### 參數  
 `str`  
 資料儲存位置  
  
 `n`  
 要讀取的最大字元數  
  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 這些函式都會傳回 `str`。  `NULL` 會傳回錯誤或一個文件關閉條件。  使用 `feof` 或 `ferror` 判斷是否發生錯誤。  如果 `str` 或 `stream` 是null指標或 `n` 小於或等於零，這些函式叫用無效參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `NULL`。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `fgets` 函式。 `str`會從輸入 `stream` 引數的字串並儲存它。  `fgets` 讀取自目前資料流位置的字元加入至，並將第一個新行字元，將資料流結尾，或直到讀取的字元數與 `n` – 1 相等， \(兩者取其先\)。  儲存於 `str` 的結果為命令列附加一個 Null 字元。  新行字元，如果讀取則在字串中。  
  
 `fgetws` 是 `fgets`的寬字元版本。  
  
 `fgetws` 分別讀入寬字元引數 `str` 對 `stream` 做為多位元組字元字串或寬字元字串，根據可能的選取文字模式或二進位模式開啟。  如需使用文字和以 Unicode 和多位元組資料流 I\/O二進位模式的詳細資訊，請參閱 [文字和二進位模式檔案 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [Unicode 文字和二進位模式的資料流 I\/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_fgetts`|`fgets`|`fgets`|`fgetws`|  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fgets`|\<stdio.h\>|  
|`fgetws`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_fgets.c  
// This program uses fgets to display  
// a line from a file on the screen.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[100];  
  
   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )  
   {  
      if( fgets( line, 100, stream ) == NULL)  
         printf( "fgets error\n" );  
      else  
         printf( "%s", line);  
      fclose( stream );  
   }  
}  
```  
  
## 輸入:crt\_fgets.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Line one.  
```  
  
## .NET Framework 對等用法  
  
-   [System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx)  
  
-   [System::IO::TextReader::ReadBlock](https://msdn.microsoft.com/en-us/library/system.io.textreader.readblock.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [gets、\_getws](../../c-runtime-library/gets-getws.md)   
 [puts、\_putws](../../c-runtime-library/reference/puts-putws.md)