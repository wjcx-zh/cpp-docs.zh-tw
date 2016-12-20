---
title: "tmpfile_s | Microsoft Docs"
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
  - "tmpfile_s"
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
  - "tmpfile_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "暫存檔案"
  - "tmpfile_s 函式"
  - "暫存檔案, 建立"
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tmpfile_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立暫存檔案。  這些是 [](../../c-runtime-library/reference/tmpfile.md "tmpfile")[CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t tmpfile_s(  
   FILE** pFilePtr  
);  
```  
  
#### 參數  
 \[out\] `pFilePtr`  
 儲存產生之指標的指標位址至資料流。  
  
## 傳回值  
 如果成功，回傳零，如果失敗，則為錯誤碼。  
  
### 錯誤狀況  
  
|`pFilePtr`|**傳回值**|`pFilePtr` **的內容**|  
|----------------|-------------|------------------------|  
|`NULL`|`EINVAL`|沒變更|  
  
 如果上述任參數驗證錯誤發生，則無效的參數會叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，會將`errno` 設為 `EINVAL`，並傳回值是`EINVAL`。  
  
## 備註  
 `tmpfile_s` 函式會建立暫存檔案並將指標對該資料流的 `pFilePtr` 引數。  暫存檔案在根目錄中建立。  除了之外，要在該目錄中建立暫存檔案，請使用 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)搭配使用 [tmpnam\_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md) 或 [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 。  
  
 如果無法開啟檔案，則 `tmpfile_s` 會寫入`NULL`給`pFilePtr` 參數 。  這個暫存檔自動刪除時，只有在檔案關閉，也就是說，當程式通常時結束，或者，呼叫 `_rmtmp` 時，會假設，在目前的工作目錄不會變更。  暫存檔案在 `w+b` \(二進位\) 讀取\/寫入模式下開啟。  
  
 如果您試圖以`tmpfile_s.`嘗試比`TMP_MAX_S`\(請參閱 STDIO.H\)更多的呼叫，會發生錯誤。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`tmpfile_s`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
> [!NOTE]
>  您必須擁有系統管理員權限，才能在 Windows Vista 中執行本範例。  
  
```  
// crt_tmpfile_s.c  
// This program uses tmpfile_s to create a  
// temporary file, then deletes this file with _rmtmp.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char tempstring[] = "String to be written";  
   int  i;  
   errno_t err;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      err = tmpfile_s(&stream);  
      if( err )  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
  **暫存檔案 1 建立**  
**暫存檔案 2 建立**  
**暫存檔案 3 建立**  
**刪除的 3 個暫存檔**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_rmtmp](../../c-runtime-library/reference/rmtmp.md)   
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)