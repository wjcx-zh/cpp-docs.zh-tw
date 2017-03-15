---
title: "getc、getwc | Microsoft Docs"
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
  - "getwc"
  - "getc"
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
  - "_gettc"
  - "getwc"
  - "_gettchar"
  - "getc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_gettc 函式"
  - "字元, 讀取"
  - "getc 函式"
  - "gettc 函式"
  - "getwc 函式"
  - "getwchar 函式"
  - "從資料流讀取字元"
  - "資料流, 讀取字元來源"
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getc、getwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料流讀取一個字元。  
  
## 語法  
  
```  
int getc(   
   FILE *stream   
);  
wint_t getwc(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 輸入資料流。  
  
## 傳回值  
 傳回讀取的字元。  為表示讀取錯誤或文件關閉條件， `getc` 會傳回 `EOF`、 `getwc` 會傳回 `WEOF`。  對於 `getc`，請使用 `ferror` 或 `feof` 來檢查錯誤或檔案結尾。  如果 `stream` 為 `NULL`，`getc` 和 `getwc`叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 `EOF`\(或 `getwc` 的 `WEOF`\)，並將 `errno` 設定為 `EINVAL`。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 每個常式從目前位置的檔案讀取單一字元並將相關檔案指標 \(如果有定義\)指向下一個字元。  這個檔案與 `stream` 相關聯。  
  
 這些函式鎖定呼叫的執行緒並具備執行緒安全。  如需非鎖定版本，請參閱 [\_getc\_nolock、\_getwc\_nolock](../../c-runtime-library/reference/getc-nolock-getwc-nolock.md)。  
  
 再來為常式特定圖例。  
  
|常式|備註|  
|--------|--------|  
|`getc`|與 `fgetc`相同，不過，實作為函式和巨集。|  
|`getwc`|`getc`寬字元版本。  讀取多位元組字元或寬字元根據是否 `stream` 在文字模式或二進位模式下開啟。|  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE 和 \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_gettc`|`getc`|`getc`|`getwc`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`getc`|\<stdio.h\>|  
|`getwc`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getc.c  
// Use getc to read a line from a file.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
    FILE* fp;  
  
    // Read a single line from the file "crt_getc.txt".   
  
    fopen_s(&fp, "crt_getc.txt", "r");  
    if (!fp)  
    {  
       printf("Failed to open file crt_getc.txt.\n");  
       exit(1);  
    }  
  
    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
  
    fclose(fp);  
}  
```  
  
## Input: crt\_getc.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Input was: Line one.  
```  
  
## .NET Framework 對等用法  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx).  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc、ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)