---
title: "fopen、_wfopen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wfopen
- fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
dev_langs:
- C++
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
caps.latest.revision: 56
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 7d432ab9e8bdb6f386eb6fe4fbb24d218d6a2071
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="fopen-wfopen"></a>fopen、_wfopen
開啟檔案。 這些函式已有更安全的版本可用，並會額外執行參數驗證且傳回錯誤碼；請參閱 [fopen_s、_wfopen_s](../../c-runtime-library/reference/fopen-s-wfopen-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
FILE *fopen(   
   const char *filename,  
   const char *mode   
);  
FILE *_wfopen(   
   const wchar_t *filename,  
   const wchar_t *mode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 檔案名稱  
  
 `mode`  
 啟用的存取類型。  
  
## <a name="return-value"></a>傳回值  
 每一個這些函式都會傳回已開啟的檔案的指標。 null 指標值表示錯誤。 若 `filename` 或 `mode` 為 `NULL` 或空字串，這些函式會觸發無效參數處理常式，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回 `NULL` ，並將 `errno` 設為 `EINVAL`。  
  
 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `fopen` 函式會開啟 `filename`所指定的檔案。 根據預設，窄的 `filename` 字串會使用 ANSI 字碼頁 (CP_ACP) 解譯。 在 Windows 桌面應用程式中，這可以透過 [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534\(v=vs.85\).aspx) 函式變更為 OEM 字碼頁 (CP_OEMCP)。 您可以使用 [AreFileApisANSI](https://msdn.microsoft.com/library/windows/desktop/aa363781\(v=vs.85\).aspx) 函式決定要使用 ANSI 或系統預設的 OEM 字碼頁來解譯 `filename` 。 `_wfopen` 是 `fopen`的寬字元版本； `_wfopen` 的引數是寬字元字串。 否則 `_wfopen` 和 `fopen` 的行為相同。 只是使用 `_wfopen` ，對於檔案資料流中使用的編碼字元集沒有作用。  
  
 `fopen` 接受執行之時在檔案系統上為有效的路徑； `fopen` 接受 UNC 路徑以及包含對應的網路磁碟機的路徑，只要執行程式碼的系統在執行時有權存取共用或對應磁碟機即可。 當您建構 `fopen`的路徑時，請確定磁碟機、路徑或網路共用可以在執行環境中使用。 您可以使用正斜線 (/) 或反斜線 (\\) 作為路徑中的目錄分隔符號。  
  
 務必檢查傳回值，在對檔案執行其他任何作業之前，查看指標是否為 NULL。 如果發生錯誤，將會設定全域變數 `errno` ，這個變數可以用來取得特定錯誤資訊。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="unicode-support"></a>Unicode 支援  
 `fopen` 支援 Unicode 檔案資料流。 若要開啟 Unicode 檔案，請將指定所需編碼方式的 `ccs` 旗標傳遞給 `fopen`，如下所示。  
  
 `FILE *fp = fopen("newfile.txt", "rt+, ccs=encoding");`  
  
 `encoding` 的允許值為 `UNICODE`、 `UTF-8`和 `UTF-16LE`。  
  
 使用 Unicode 模式開啟檔案時，請輸入函式，將從檔案讀取的資料，轉譯為儲存為類型 `wchar_t`的 UTF-16 資料。 寫入檔案的函式會以 Unicode 模式開啟，但包含儲存為類型 `wchar_t`之 UTF-16 資料的緩衝區除外。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元組會導致 [參數驗證](../../c-runtime-library/parameter-validation.md) 錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。  
  
 如果檔案已經存在，而且已開啟來進行讀取或附加，則位元順序標記 (BOM) (如果已在檔案中) 會決定編碼方式。 BOM 編碼方式的優先順序高於 `ccs` 旗標所指定的編碼方式。 當 BOM 不存在或檔案為新檔案時，只能使用 `ccs` 編碼方式。  
  
> [!NOTE]
>  BOM 偵測只適用於以 Unicode 模式 (也就是，透過傳遞 `ccs` 旗標) 開啟的檔案。  
  
 下表摘要說明可用於各種指定給 `ccs` 及檔案中位元順序標記之 `fopen` 旗標的模式。  
  
### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>根據 ccs 旗標和 BOM 使用的編碼方式  
  
|`ccs` 旗標|沒有 BOM (或新檔案)|BOM：UTF-8|BOM：UTF-16|  
|----------------|----------------------------|-----------------|------------------|  
|`UNICODE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
|`UTF-8`|`UTF-8`|`UTF-8`|`UTF-16LE`|  
|`UTF-16LE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
  
 開啟以供在 Unicode 模式下寫入的檔案會有 BOM 自動寫入其中。  
  
 如果 `mode` 為 "`a, ccs=<encoding>`"，則 `fopen` 會先嘗試同時使用讀取和寫入存取來開啟檔案。 如果這個動作成功，則函式會讀取 BOM 以判斷檔案的編碼方式，如果失敗，則函式會使用檔案的預設編碼方式。 在任一情況下， `fopen` 都會接著使用唯寫存取重新開啟檔案。 (這只適用於 `a` 模式，但不適用於 `a+` 模式)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfopen`|`fopen`|`fopen`|`_wfopen`|  
  
 字元字串 `mode` 會指定對檔案要求的存取類型，如下所示。  
  
 `"r"`  
 開啟以讀取。 如果檔案不存在或找不到， `fopen` 呼叫就會失敗。  
  
 `"w"`  
 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。  
  
 `"a"`  
 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。  
  
 `"r+"`  
 開啟以進行讀取和寫入。 檔案必須存在。  
  
 `"w+"`  
 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。  
  
 `"a+"`  
 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。  
  
 使用 `"a"` 存取類型或 `"a+"` 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。 檔案指標可以使用 `fseek` 或 `rewind`重新調整位置，但是在執行任何寫入作業之前，一律會移回至檔案結尾。 因此，無法覆寫現有資料。  
  
 在附加到檔案之前， `"a"` 模式不會移除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 `"a+"` 模式會在附加到檔案之前移除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 附加至以 CTRL+Z EOF 標記終止的資料流檔案時，需要 `"a+"` 模式。  
  
 指定 `"r+"`、 `"w+"`或 `"a+"` 存取類型時，會同時啟用讀取和寫入 (表示檔案是要開啟以供「更新」之用)。 不過，當您從讀取切換為寫入時，輸入作業一定會遇到 EOF 標記。 如果沒有 EOF，您就必須使用檔案定位函式的介入呼叫。 檔案定位函式包括 `fsetpos`、 `fseek`和 `rewind`。 當您從寫入切換為讀取時，您必須使用 `fflush` 或檔案定位函式的介入呼叫。  
  
 除了先前的值之外，還可以將下列字元附加至 `mode` ，指定新行字元的轉譯模式。  
  
 `t`  
 以文字 (已轉譯) 模式開啟。 在此模式下，CTRL+Z 會在輸入時解譯成 EOF 字元。 在使用 `"a+"`開啟為讀取/寫入的檔案中， `fopen` 會檢查檔案結尾是否有 CTRL+Z，並盡可能加以移除。 之所以這樣做，是因為使用 `fseek` 和 `ftell` 在以 CTRL+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不正確的行為。  
  
 在文字模式下，歸位字元傳回換行字元組合會轉譯成單一換行字元上輸入，然後換行字元會轉譯為歸位字元傳回換行字元組合，在輸出上。 Unicode 資料流 I/O 函式在文字模式 (預設) 下運作時，會假設來源或目的資料流是多位元組字元的序列。 因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 (就像呼叫 `mbtowc` 函式一樣)。 基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 (就像呼叫 `wctomb` 函式一樣)。  
  
 `b`  
 以二進位 (未轉譯) 模式開啟；抑制涉及歸位字元和換行字元的轉譯。  
  
 如果 `t` 中未指定 `b` 或 `mode`，則預設轉譯模式由全域變數 [_fmode](../../c-runtime-library/fmode.md)定義。 如果引數前置 `t` 或 `b` ，則函式失敗並傳回 `NULL`。  
  
 如需如何在 Unicode 及多位元組資料流 I/O 中使用文字與二進位模式的詳細資訊，請參閱 [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 及 [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。  
  
 `c`  
 啟用關聯 `filename` 的認可旗標，以便在呼叫 `fflush` 或 `_flushall` 時，將檔案緩衝區的內容直接寫入磁碟。  
  
 `n`  
 將關聯 `filename` 的認可旗標重設為 "no-commit"。 這是預設值。 如果將程式與 COMMODE.OBJ 連結，也會覆寫全域認可旗標。 除非您明確連結程式與 COMMODE.OBJ，否則全域認可旗標的預設值為 "no-commit" (請參閱 [Link Options](../../c-runtime-library/link-options.md))。  
  
 `N`  
 指定子處理序不繼承檔案。  
  
 `S`  
 指定針對但不限於磁碟的循序存取進行快取最佳化。  
  
 `R`  
 指定針對但不限於磁碟的隨機存取進行快取最佳化。  
  
 `T`  
 指定檔案做為暫存檔。 可能的話，不將其清除至磁碟。  
  
 `D`  
 指定檔案做為暫存檔。 當最後一個檔案指標關閉時，將其刪除。  
  
 `ccs=ENCODING`  
 指定這個檔案要使用的編碼字元集 (`UTF-8`、 `UTF-16LE`或 `UNICODE`)。 如果您想要使用 ANSI 編碼方式，請保持為未指定。  
  
 `mode` 及 `fopen` 中所用之 `_fdopen` 字串的有效字元，會與 `oflag` _open [及](../../c-runtime-library/reference/open-wopen.md) _sopen [中所用的](../../c-runtime-library/reference/sopen-wsopen.md)引數相對應，如下所示。  
  
|模式字串中的字元|`_open`/`_sopen` 的對等 `oflag` 值|  
|-------------------------------|----------------------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND`(通常為 `_O_WRONLY &#124; _O_CREAT &#124; _O_APPEND`)|  
|`a+`|`_O_RDWR &#124; _O_APPEND` (通常為 `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT` )|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY`(通常為 `_O_WRONLY &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`w+`|`_O_RDWR`(通常為 `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`)|  
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
  
 如果您使用 `rb` 模式，沒有移植程式碼的需要，並且打算讀取大部分大型檔案或者不在意網路效能時，您也可以考慮是否要使用 Win32 記憶體對應檔案做為選項。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`fopen`|\<stdio.h>|  
|`_wfopen`|\<stdio.h> 或 \<wchar.h>|  
  
 `_wfopen` 是 Microsoft 擴充功能。 如需相容性的詳細資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。  
  
 `c`, `n`, `t`, `S`, `R`, `T`和 `D` `mode` 選項是 `fopen` 和 `_fdopen` 和 should not be used where ANSI portability is desired.  
  
## <a name="example"></a>範例  
 下列程式會開啟兩個檔案。  這會使用 `fclose` 關閉第一個檔案，並使用 `_fcloseall` 關閉所有剩下的檔案。  
  
```C  
// crt_fopen.c  
// compile with: /W3  
// This program opens two files. It uses  
// fclose to close the first file and  
// _fcloseall to close all remaining files.  
  
#include <stdio.h>  
  
FILE *stream, *stream2;  
  
int main( void )  
{  
   int numclosed;  
  
   // Open for read (will fail if file "crt_fopen.c" does not exist)  
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996  
   // Note: fopen is deprecated; consider using fopen_s instead  
      printf( "The file 'crt_fopen.c' was not opened\n" );  
   else  
      printf( "The file 'crt_fopen.c' was opened\n" );  
  
   // Open for write   
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996  
      printf( "The file 'data2' was not opened\n" );  
   else  
      printf( "The file 'data2' was opened\n" );  
  
   // Close stream if it is not NULL   
   if( stream)  
   {  
      if ( fclose( stream ) )  
      {  
         printf( "The file 'crt_fopen.c' was not closed\n" );  
      }  
   }  
  
   // All other files are closed:   
   numclosed = _fcloseall( );  
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );  
}  
```  
  
```Output  
The file 'crt_fopen.c' was opened  
The file 'data2' was opened  
Number of files closed by _fcloseall: 1  
```  
  
## <a name="example"></a>範例  
 下列程式會在使用 Unicode 編碼方式的文字模式下建立檔案 (如果存在則覆寫)。  然後將兩個字串寫入檔案並關閉檔案。 輸出是名為 _wfopen_test.xml 的檔案，其中包含來自輸出區域的資料。  
  
```C  
// crt__wfopen.c  
// compile with: /W3  
// This program creates a file (or overwrites one if  
// it exists), in text mode using Unicode encoding.  
// It then writes two strings into the file  
// and then closes the file.  
  
#include <stdio.h>  
#include <stddef.h>  
#include <stdlib.h>  
#include <wchar.h>  
  
#define BUFFER_SIZE 50  
  
int main(int argc, char** argv)  
{  
    wchar_t str[BUFFER_SIZE];  
    size_t  strSize;  
    FILE*   fileHandle;  
  
    // Create an the xml file in text and Unicode encoding mode.  
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996  
    // Note: _wfopen is deprecated; consider using _wfopen_s instead  
    {  
        wprintf(L"_wfopen failed!\n");  
        return(0);  
    }  
  
    // Write a string into the file.  
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");  
    strSize = wcslen(str);  
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)  
    {  
        wprintf(L"fwrite failed!\n");  
    }  
  
    // Write a string into the file.  
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");  
    strSize = wcslen(str);  
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)  
    {  
        wprintf(L"fwrite failed!\n");  
    }  
  
    // Close the file.  
    if (fclose(fileHandle))  
    {  
        wprintf(L"fclose failed!\n");  
    }  
    return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen、_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [freopen、_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)   
 [_sopen、_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)
