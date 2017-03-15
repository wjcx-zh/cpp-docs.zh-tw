---
title: "fclose、_fcloseall | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fclose"
  - "_fcloseall"
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
  - "fclose"
  - "_fcloseall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fclose 函式"
  - "資料流，關閉"
  - "_fcloseall 函式"
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# fclose、_fcloseall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

關閉資料流 \(`fclose`\) 或已經關閉所有開啟的資料流 \(`_fcloseall`\)。  
  
## 語法  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 資料流，則成功關閉，則`fclose` 會傳回 0。  `_fcloseall` 會關閉資料流總數。  兩個函式表示錯誤的傳回 `EOF` 。  
  
## 備註  
 `fclose` 函式會關閉 `stream`。  如果 `stream` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行， `fclose` 會設定 `errno` 為 `EINVAL` 並回傳 `EOF` 。  建議 `stream` 指標在呼叫這個函式一律先進行檢查。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
 `_fcloseall` 函式會關閉所有除了 `stdin`， `stdout`， `stderr` \(而且， MS\-DOS 中， `_stdaux` 和 `_stdprn`\) 中開啟的資料流。  它也會關閉並刪除 `tmpfile`建立的所有暫存檔案。  在兩個函式，所有緩衝區與資料流關閉之前清除。  系統配置緩衝區，在資料流關閉時，釋放。  不會自動釋放由使用者的緩衝區具有指定 `setbuf` 的 `setvbuf` 。  
  
 **Note:** ，當這些函式來關閉資料流時，基礎檔案描述項和作業系統檔案控制代碼 \(或\) 關閉通訊端，以及資料流。  因此，在中，如果檔案初次開啟為檔案控制代碼或檔案描述項和關閉 `fclose`，也不要呼叫 `_close` 關閉檔案描述;不要呼叫 Win32 函式 `CloseHandle` 關閉檔案控制代碼。  
  
 `fclose` 和 `_fcloseall` 以防止所包含的程式碼受到干擾防止其他執行緒。  如需非鎖定的`fclose`版本，請參閱`_fclose_nolock` 。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fclose`|\<stdio.h\>|  
|`_fcloseall`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [fopen](../../c-runtime-library/reference/fopen-wfopen.md) 的範例。  
  
## .NET Framework 對等用法  
  
-   [System::IO::BinaryReader::Close](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.close.aspx)  
  
-   [System::IO::BinaryWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.close.aspx)  
  
-   [System::IO::StringReader::Close](https://msdn.microsoft.com/en-us/library/system.io.stringreader.close.aspx)  
  
-   [System::IO::StringWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.stringwriter.close.aspx)  
  
-   [System::IO::Stream::Close](https://msdn.microsoft.com/en-us/library/system.io.stream.close.aspx)  
  
-   [System::IO::StreamReader::Close](https://msdn.microsoft.com/en-us/library/system.io.streamreader.close.aspx)  
  
-   [System::IO::StreamWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.close.aspx)  
  
-   [System::IO::TextReader::Close](https://msdn.microsoft.com/en-us/library/system.io.textreader.close.aspx)  
  
-   [System::IO::TextWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.textwriter.close.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)