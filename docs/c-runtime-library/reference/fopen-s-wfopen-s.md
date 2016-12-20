---
title: "fopen_s、_wfopen_s | Microsoft Docs"
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
  - "_wfopen_s"
  - "fopen_s"
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
  - "fopen_s"
  - "_tfopen_s"
  - "_wfopen_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tfopen_s 函式"
  - "_wfopen_s 函式"
  - "檔案 [C++], 開啟"
  - "fopen_s 函式"
  - "開啟檔案, 用於檔案 I/O"
  - "tfopen_s 函式"
  - "Unicode [C++], 建立檔案"
  - "Unicode [C++], 檔案"
  - "Unicode [C++], 寫入檔案"
  - "wfopen_s 函式"
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
caps.latest.revision: 41
caps.handback.revision: 39
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fopen_s、_wfopen_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開啟檔案。  這些版本的 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md) 具有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t fopen_s(   
   FILE** pFile,  
   const char *filename,  
   const char *mode   
);  
errno_t _wfopen_s(  
   FILE** pFile,  
   const wchar_t *filename,  
   const wchar_t *mode   
);  
```  
  
#### 參數  
 \[輸出\] `pFile`  
 指向檔案指標 \(將接收指向已開啟檔案之指標\) 的指標。  
  
 \[in\] `filename`  
 檔案名稱。  
  
 \[in\] `mode`  
 允許的存取類型。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  如需這些傳回碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 錯誤狀況  
  
|`pFile`|`filename`|`mode`|傳回值|`pFile` 的內容。|  
|-------------|----------------|------------|---------|------------------|  
|`NULL`|任何|任何|`EINVAL`|未變更|  
|任何|`NULL`|任何|`EINVAL`|未變更|  
|any|any|NULL|`EINVAL`|未變更|  
  
## 備註  
 `fopen_s` 和 `_wfopen_s` 所開啟的檔案無法共用。  如果您要求該檔案要是可共用的，請使用 [\_fsopen、\_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md) 搭配適當的共用模式常數 — 例如，用於讀取\/寫入共用的 `_SH_DENYNO`。  
  
 `fopen_s` 函式會開啟 `filename` 所指定的檔案。  `_wfopen_s` 是 `fopen_s` 的寬字元版本；`_wfopen_s` 的引數是寬字元字串。  否則，`_wfopen_s` 和 `fopen_s` 的行為即會相同。  
  
 `fopen_s` 接受執行之時在檔案系統上為有效的路徑；`fopen_s` 接受 UNC 路徑以及包含對應的網路磁碟機的路徑，只要執行程式碼的系統在執行時有權存取共用或對應的網路磁碟機即可。  當您建構 `fopen_s` 的路徑時，請不要假設磁碟機、路徑或網路共用在執行環境中可供使用。  您可以使用正斜線 \(\/\) 或反斜線 \(\\\) 做為路徑中的目錄分隔符號。  
  
 這些函式會驗證它們的參數。  如果 `pFile`、`filename` 或 `mode` 是 null 指標，則此函式會產生無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 請務必檢查傳回值，在對檔案執行任何進一步作業之前，查看此函式是否已成功。  如果發生錯誤，則傳回錯誤碼，且設定全域變數 `errno`。  如需詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## Unicode 支援  
 `fopen_s` 支援 Unicode 檔案資料流。  若要開啟新的或現有的 Unicode 檔案，請將指定所需編碼方式的 `ccs` 旗標傳遞給 `fopen_s`：  
  
 `fopen_s(&fp, "newfile.txt", "rw,`   `ccs=`  `encoding` `");`  
  
 `encoding` 的允許值為 `UNICODE`、`UTF-8` 和 `UTF-16LE`。  如果未對 `encoding` 指定值，則 `fopen_s` 會使用 ANSI 編碼方式。  
  
 如果檔案已經存在，而且已開啟來進行讀取或附加，則位元順序標記 \(BOM\) \(如果已在檔案中\) 會決定編碼方式。  BOM 編碼方式的優先順序高於 `ccs` 旗標所指定的編碼方式。  當 BOM 不存在或如果檔案為新檔案時，只能使用 `ccs` 編碼方式。  
  
> [!NOTE]
>  BOM 偵測只適用於以 Unicode 模式 \(也就是透過傳遞 `ccs` 旗標\) 開啟的檔案。  
  
 下表摘要說明指定給 `fopen_s` 及檔案中位元順序標記之各種 `ccs` 旗標的模式。  
  
### 根據 ccs 旗標和 BOM 使用的編碼方式  
  
|`ccs` 旗標|沒有 BOM \(或新檔案\)|BOM：UTF\-8|BOM：UTF\-16|  
|--------------|---------------------|----------------|-----------------|  
|`UNICODE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
|`UTF-8`|`UTF-8`|`UTF-8`|`UTF-16LE`|  
|`UTF-16LE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
  
 開啟以供在 Unicode 模式下寫入的檔案會有 BOM 自動寫入其中。  
  
 如果 `mode` 為 "`a, ccs=<encoding>`"，則 `fopen_s` 會先嘗試同時以讀取存取和寫入存取來開啟檔案。  如果成功，則函式會讀取 BOM 以判斷檔案的編碼方式，如果不成功，則函式會使用檔案的預設編碼方式。  在任一情況下，`fopen_s` 都會接著以唯寫存取重新開啟檔案。  \(這只適用於 `a` 模式，但不適用於 `a+`。\)  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfopen_s`|`fopen_s`|`fopen_s`|`_wfopen_s`|  
  
 字元字串 `mode` 會指定對檔案要求的存取類型，如下所示。  
  
 `"r"`  
 開啟以讀取。  如果檔案不存在或找不到，`fopen_s` 呼叫就會失敗。  
  
 `"w"`  
 開啟空白檔案以寫入。  如果檔案存在，其內容會遭到銷毀。  
  
 `"a"`  
 開啟以供在檔案結尾寫入 \(附加\)，並且在新資料寫入檔案之前，不會移除 EOF 標記。  如果該檔案不存在，則建立檔案。  
  
 `"r+"`  
 開啟以進行讀取和寫入。  \(檔案必須存在。\)  
  
 `"w+"`  
 開啟空白檔案以進行讀取和寫入。  如果檔案存在，其內容會遭到銷毀。  
  
 `"a+"`  
 開啟以進行讀取和附加。  此附加作業包含在將新資料寫入檔案之前移除 EOF 標記，且寫入完成後會復原 EOF 標記。  如果該檔案不存在，則建立檔案。  
  
 使用 `"a"` 或 `"a+"` 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。  檔案指標可以使用 `fseek` 或 `rewind` 重新調整位置，但是在執行任何寫入作業之前，永遠會移回至檔案結尾，如此會無法覆寫現有的資料。  
  
 在附加到檔案之前，`"a"` 模式不會移除 EOF 標記。  進行附加之後，MS\-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。  在附加到檔案之前，`"a+"` 模式會移除 EOF 標記。  附加之後，MS\-DOS TYPE 命令會顯示檔案中的所有資料。  附加至使用 CTRL\+Z EOF 標記終止的資料流檔案時，需要 `"a+"` 模式。  
  
 指定 `"r+",`、`"w+",` 或 `"a+"` 存取類型時，同時允許讀取和寫入。  \(表示檔案是要開啟以供「更新」之用。\) 不過，當您從讀取切換為寫入時，輸入作業一定會遇到 EOF 標記。  如果沒有 EOF，您就必須使用檔案定位函式的介入呼叫。  檔案定位函式包含 `fsetpos`、`fseek` 和 `rewind`。  當您從寫入切換為讀取時，您必須使用 `fflush` 或檔案定位函式的介入呼叫。  
  
 除了上面的值之外，還可以將下列字元包含在 `mode`，指定新行字元的轉譯模式：  
  
 `t`  
 以文字 \(已轉譯\) 模式開啟。  在這個模式中，Ctrl\+Z 會在輸入中解譯成檔案結尾字元。  在為了以 `"a+"` 讀取\/寫入而開啟的檔案中，`fopen_s` 會盡可能檢查檔案結尾是否有 Ctrl\+Z，並加以移除。  之所以這樣做，是因為使用 `fseek` 和 `ftell` 在以 Ctrl\+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不當行為。  
  
 此外在文字模式下，歸位字元與換行字元組合會在輸入中轉譯成單一換行字元，而換行字元會在輸出中轉譯成歸位字元與換行字元組合。  Unicode 資料流 I\/O 函式在文字模式 \(預設\) 下運作時，會假設來源或目的資料流是多位元組字元的序列。  因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 \(就像呼叫 `mbtowc` 函式一樣\)。  基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 \(就像呼叫 `wctomb` 函式一樣\)。  
  
 `b`  
 以二進位 \(未轉譯\) 模式開啟；抑制涉及歸位字元和換行字元的轉譯。  
  
 如果 `t` 中未指定 `b` 或 `mode`，則預設轉譯模式由全域變數 [\_fmode](../../c-runtime-library/fmode.md) 定義。  如果引數前置 `t` 或 `b`，則函式失敗並傳回 `NULL`。  
  
 如需在 Unicode 和多位元組資料流 I\/O 使用文字和二進位模式的詳細資訊，請參閱[文字和二進位模式檔案 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文字和二進位模式的 Unicode 資料流 I\/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。  
  
 `c`  
 啟用關聯 `filename` 的認可旗標，以便在呼叫 `fflush` 或 `_flushall` 時，將檔案緩衝區的內容直接寫入磁碟。  
  
 `n`  
 將關聯 `filename` 的認可旗標重設為 "no\-commit"。 這是預設值。  如果將程式與 COMMODE.OBJ 連結，也會覆寫全域認可旗標。  除非您明確將程式與 COMMODE.OBJ 連結，否則全域認可旗標預設值為 "no\-commit" \(請參閱[連結選項](../../c-runtime-library/link-options.md)\)。  
  
 `N`  
 指定子處理序不繼承檔案。  
  
 `S`  
 指定針對但不限於磁碟的循序存取進行快取最佳化。  
  
 `R`  
 指定針對但不限於磁碟的隨機存取進行快取最佳化。  
  
 `T`  
 指定檔案做為暫存檔。  可能的話，不將其清除至磁碟。  
  
 `D`  
 指定檔案做為暫存檔。  當最後一個檔案指標關閉時，將其刪除。  
  
 `ccs=ENCODING`  
 指定要用於此檔案之編碼的字元集 \(UTF\-8、UTF\-16LE 和 UNICODE\)。  如果您想要使用 ANSI 編碼方式，請將此保持為未指定。  
  
 `fopen_s` 和 `_fdopen` 中所用 `mode` 字串的有效字元會對應用於 [\_open](../../c-runtime-library/reference/open-wopen.md) 和 [\_sopen](../../c-runtime-library/reference/sopen-wsopen.md) 的 `oflag` 引數，如下所示。  
  
|模式字串中的字元|`oflag`\/`_open` 的對應 `_sopen` 值|  
|--------------|-------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND` \(通常為 `_O_WRONLY &#124; _O_CREAT &#124;``_O_APPEND`\)|  
|`a+`|`_O_RDWR &#124; _O_APPEND` \(通常為 `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT` \)|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY` \(通常為 `_O_WRONLY &#124;``_O_CREAT &#124; _O_TRUNC`\)|  
|`w+`|`_O_RDWR`\(通常為 `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`\)|  
|`b`|`_O_BINARY`|  
|`t`|`_O_TEXT`|  
|`c`|無|  
|`n`|無|  
|`S`|`_O_SEQUENTIAL`|  
|`R`|`_O_RANDOM`|  
|`T`|`_O_SHORTLIVED`|  
|`D`|`_O_TEMPORARY`|  
|`ccs=UNICODE`|`_O_WTEXT`|  
|`ccs=UTF-8`|`_O_UTF8`|  
|`ccs=UTF-16LE`|`_O_UTF16`|  
  
 如果您正使用 `rb` 模式，不需要移植程式碼，且預期會讀取大量的檔案及\/或不在意網路效能，則對應 Win32 檔案的記憶體也可能是個選項。  
  
## 需求  
  
|函式|必要的標頭|  
|--------|-----------|  
|`fopen_s`|\<stdio.h\>|  
|`_wfopen_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
 `c`、`n` 和 `t` `mode` 選項是 `fopen_s` 和 `_fdopen` 的 Microsoft 擴充功能，不應在需要 ANSI 可攜性的情況中使用。  
  
## 範例  
  
```  
// crt_fopen_s.c  
// This program opens two files. It uses  
// fclose to close the first file and  
// _fcloseall to close all remaining files.  
  
#include <stdio.h>  
  
FILE *stream, *stream2;  
  
int main( void )  
{  
   errno_t err;  
  
   // Open for read (will fail if file "crt_fopen_s.c" does not exist)  
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );  
   if( err == 0 )  
   {  
      printf( "The file 'crt_fopen_s.c' was opened\n" );  
   }  
   else  
   {  
      printf( "The file 'crt_fopen_s.c' was not opened\n" );  
   }  
  
   // Open for write   
   err = fopen_s( &stream2, "data2", "w+" );  
   if( err == 0 )  
   {  
      printf( "The file 'data2' was opened\n" );  
   }  
   else  
   {  
      printf( "The file 'data2' was not opened\n" );  
   }  
  
   // Close stream if it is not NULL   
   if( stream )  
   {  
      err = fclose( stream );  
      if ( err == 0 )  
      {  
         printf( "The file 'crt_fopen_s.c' was closed\n" );  
      }  
      else  
      {  
         printf( "The file 'crt_fopen_s.c' was not closed\n" );  
      }  
   }  
  
   // All other files are closed:  
   int numclosed = _fcloseall( );  
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );  
}  
```  
  
  **已開啟檔案 'crt\_fopen\_s.c'**  
**已開啟檔案 'data2'**  
**\_fcloseall 關閉的檔案數目：1**   
## .NET Framework 對等用法  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.%23ctor%2A>  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [\_fileno](../../c-runtime-library/reference/fileno.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)