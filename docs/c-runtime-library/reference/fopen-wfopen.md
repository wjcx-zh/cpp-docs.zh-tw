---
title: fopen、_wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: d468226028928e3edfe67cc7f9b9eec06e06bd56
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914882"
---
# <a name="fopen-_wfopen"></a>fopen、_wfopen

開啟檔案。 這些函式已有更安全的版本可用，並會額外執行參數驗證且傳回錯誤碼；請參閱 [fopen_s、_wfopen_s](fopen-s-wfopen-s.md)。

## <a name="syntax"></a>語法

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>參數

*名稱*<br/>
檔案名稱

*mode*<br/>
啟用的存取類型。

## <a name="return-value"></a>傳回值

每一個這些函式都會傳回已開啟的檔案的指標。 null 指標值表示錯誤。 如果*filename*或*mode*是**Null**或空字串，這些函式會觸發不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回**Null** ，並將**Errno**設為**EINVAL**。

如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Fopen**函數會開啟*filename*所指定的檔案。 根據預設，會使用 ANSI 字碼頁（CP_ACP）來解讀窄的*filename*字串。 在 Windows 桌面應用程式中，這可以透過 [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) 函式變更為 OEM 字碼頁 (CP_OEMCP)。 您可以使用[AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi)函數來判斷是否使用 ANSI 或系統預設的 OEM 字碼頁來解讀*filename* 。 **_wfopen**是寬字元版本的**fopen**;**_wfopen**的引數是寬字元字串。 否則， **_wfopen**和**fopen**的行為相同。 只使用 **_wfopen**不會影響檔案資料流程中使用的編碼字元集。

在執行時， **fopen**會接受在檔案系統上有效的路徑;**fopen**接受 UNC 路徑和包含對應網路磁碟機機的路徑，前提是執行程式碼的系統在執行時有權存取共用或對應的磁片磁碟機。 當您為**fopen**建立路徑時，請確定磁片磁碟機、路徑或網路共用會在執行環境中使用。 您可以使用正斜線 (/) 或反斜線 (\\) 作為路徑中的目錄分隔符號。

務必檢查傳回值，在對檔案執行其他任何作業之前，查看指標是否為 NULL。 如果發生錯誤，則會設定全域變數**errno** ，並可用來取得特定錯誤資訊。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="unicode-support"></a>Unicode 支援

**fopen**支援 Unicode 檔案資料流程。 若要開啟 Unicode 檔案，請將指定所需編碼方式的**ccs**旗標傳遞給**fopen**，如下所示。

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=**_encoding_**");**

允許的*編碼*值為**UNICODE**、 **utf-8**和**utf-16le**。

當以 Unicode 模式開啟檔案時，輸入函式會將從檔案讀取的資料轉譯為儲存為類型**wchar_t**的 utf-16 資料。 寫入以 Unicode 模式開啟之檔案的函式，會預期包含以類型**wchar_t**儲存之 utf-16 資料的緩衝區。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元的位元組，會導致[參數驗證](../../c-runtime-library/parameter-validation.md)錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。

如果檔案已經存在，而且已開啟來進行讀取或附加，則位元順序標記 (BOM) (如果已在檔案中) 會決定編碼方式。 BOM 編碼優先于**ccs**旗標所指定的編碼方式。 只有在沒有 BOM 存在或檔案是新檔案時，才會使用**ccs**編碼。

> [!NOTE]
> BOM 偵測只適用于以 Unicode 模式（也就是藉由傳遞**ccs**旗標）開啟的檔案。

下表摘要說明在檔案中提供給**fopen**和位元組順序標記的各種**ccs**旗標所使用的模式。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>根據 ccs 旗標和 BOM 使用的編碼方式

|ccs 旗標|沒有 BOM (或新檔案)|BOM：UTF-8|BOM：UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

開啟以供在 Unicode 模式下寫入的檔案會有 BOM 自動寫入其中。

如果*mode*是 **"a，ccs =**_encoding_**"**， **fopen**會先嘗試使用讀取和寫入存取來開啟檔案。 如果這個動作成功，則函式會讀取 BOM 以判斷檔案的編碼方式，如果失敗，則函式會使用檔案的預設編碼方式。 不論是哪一種情況， **fopen**都會使用「僅限寫入」存取來重新開啟檔案。 （這只適用于「 **a** 」模式，而不**是「a +** 」模式）。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

字元字串*模式*會指定針對檔案要求的存取類型，如下所示。

|*mode*|存取|
|-|-|
| **r** | 開啟以讀取。 如果檔案不存在或找不到， **fopen**呼叫將會失敗。 |
| **寬** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **為** | 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。 |
| **"r +"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w +"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a +"** | 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。 |

使用 **"a"** 存取類型或 **"a +"** 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。 您可以使用[fseek](fseek-fseeki64.md) [或倒轉](rewind.md)來重新置放檔案指標，但是在執行任何寫入作業之前，一律會移回至檔案結尾。 因此，無法覆寫現有資料。

「 **A** 」模式在附加至檔案之前，不會移除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 在附加到檔案之前， **"a +"** 模式會移除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 附加至以 CTRL + Z EOF 標記終止的資料流程檔案時，需要 **"a +"** 模式。

指定 **"r +"**、 **"w +"** 或 **"a +"** 存取類型時，會同時啟用讀取和寫入（此檔案稱為「更新」）。 不過，當您從讀取切換為寫入時，輸入作業一定會遇到 EOF 標記。 如果沒有 EOF，您就必須使用檔案定位函式的介入呼叫。 檔案定位函式為**fsetpos**、 [fseek](fseek-fseeki64.md)和倒轉[。](rewind.md) 當您從寫入切換為讀取時，您必須使用**fflush**或檔案定位函式的中間呼叫。

除了先前的值之外，還可以將下列字元附加至*模式*，以指定分行符號的轉譯模式。

|*模式*修飾詞|轉譯模式|
|-|-|
| **而已** | 以文字 (已轉譯) 模式開啟。 |
| **位元組** | 以二進位（未轉譯）模式開啟;會隱藏涉及回車和換行字元的翻譯。 |

在文字模式中，CTRL + Z 會在輸入時轉譯為 EOF 字元。 在使用 **"a +"** 開啟以進行讀取/寫入的檔案中， **fopen**會在檔案結尾檢查是否有 CTRL + Z，並加以移除（如果可能的話）。 這是因為使用[fseek](fseek-fseeki64.md)和**FTELL**在以 CTRL + Z 結尾的檔案內移動，可能會導致[fseek](fseek-fseeki64.md)在檔案結尾附近的行為不正確。

在文字模式中，會將換行字元組合轉譯成單行輸入的單行摘要，而換行字元則會轉譯為輸出上的換行分行符號組合。 Unicode 資料流 I/O 函式在文字模式 (預設) 下運作時，會假設來源或目的資料流是多位元組字元的序列。 因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 (就像呼叫 **mbtowc** 函式一樣)。 基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 (就像呼叫 **wctomb** 函式一樣)。

如果未在*模式*中指定**t**或**b** ，預設的轉譯模式會由全域變數[_fmode](../../c-runtime-library/fmode.md)定義。 如果**t**或**b**前面加上引數，則函式會失敗並傳回**Null**。

如需如何在 Unicode 及多位元組資料流 I/O 中使用文字與二進位模式的詳細資訊，請參閱 [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 及 [文字和二進位模式的 Unicode 資料流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

下列選項可以附加至*模式*，以指定其他行為。

|*模式*修飾詞|行為|
|-|-|
| **c** | 啟用相關聯*檔案名*的認可旗標，以便在呼叫**fflush**或 **_flushall**時，將檔案緩衝區的內容直接寫入磁片。 |
| **n** | 將相關聯*檔案名*的認可旗標重設為「未認可」。 這是預設值。 如果將程式與 COMMODE.OBJ 連結，也會覆寫全域認可旗標。 除非您明確連結程式與 COMMODE.OBJ，否則全域認可旗標的預設值為 "no-commit" (請參閱[連結選項](../../c-runtime-library/link-options.md))。 |
| **位** | 指定子處理序不繼承檔案。 |
| **今日** | 指定針對但不限於磁碟的循序存取進行快取最佳化。 |
| **R** | 指定針對但不限於磁碟的隨機存取進行快取最佳化。 |
| **T** | 指定檔案做為暫存檔。 可能的話，不將其清除至磁碟。 |
| **D** | 指定檔案做為暫存檔。 當最後一個檔案指標關閉時，將其刪除。 |
| **ccs=**_encoding_ | 指定這個檔案要使用的編碼字元集（ **utf-8**、 **Utf utf-16le**或**UNICODE**的其中一個）。 如果您想要使用 ANSI 編碼方式，請保持為未指定。 |

**Fopen**和 **_fdopen**中所使用之*模式*字串的有效字元，會對應至[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)中使用的*oflag*引數，如下所示。

|*模式*字串中的字元|Open/\_sopen 的\_對等*oflag*值|
|-------------------------------|----------------------------------------------------|
|**為**|**\_O\_WRONLY** &#124; ** \_o\_附加**（通常** \_是\_o WRONLY** &#124; ** \_ \_o**會** \_&#124;\_o append**）|
|**a +**|**\_O\_RDWR** &#124; ** \_o\_附加**（通常** \_是\_O RDWR** &#124; ** \_ \_o 附加**&#124; ** \_o\_ ** ）|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** （通常** \_是\_o WRONLY** &#124; ** \_ \_o**會** \_&#124;\_o TRUNC**）|
|**w +**|**\_O\_RDWR** （通常** \_是\_o RDWR** &#124; ** \_ \_o**會** \_&#124;\_o TRUNC**）|
|**位元組**|**\_O\_二進位**|
|**而已**|**\_O\_文字**|
|**c**|無|
|**n**|無|
|**今日**|**\_O\_順序**|
|**R**|**\_O\_隨機**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_暫存**|
|**ccs=UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs=UTF-16LE**|**\_O\_UTF16**|

如果您使用的是**rb**模式，則不需要移植您的程式碼，而且如果您想要讀取大部分大型檔案或不在意網路效能，您也可以考慮是否要使用記憶體對應的 Win32 檔案做為選項。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> 或 \<wchar.h>|

**_wfopen**是 Microsoft 擴充功能。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**C**、 **n**、 **t**、 **S**、 **R**、 **t**和**D** *模式*選項是適用于**fopen**和 **_fdopen**的 Microsoft 擴充功能，不應在需要 ANSI 可攜性的情況下使用。

## <a name="example-1"></a>範例 1

下列程式會開啟兩個檔案。  它會使用**fclose**來關閉第一個檔案，然後 **_fcloseall**關閉所有剩餘的檔案。

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

## <a name="example-2"></a>範例 2

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

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
