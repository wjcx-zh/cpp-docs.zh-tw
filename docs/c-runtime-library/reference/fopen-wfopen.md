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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4b9fa6542996b2c16128a841e2611b85e995be2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346413"
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

*檔案名稱*<br/>
檔案名稱

*模式*<br/>
啟用的存取類型。

## <a name="return-value"></a>傳回值

每一個這些函式都會傳回已開啟的檔案的指標。 null 指標值表示錯誤。 如果*檔案名稱*或*模式*為**NULL**或空字串,這些函數將觸發無效的參數處理程式,這在[參數驗證](../../c-runtime-library/parameter-validation.md)中描述。 如果允許繼續執行,這些函數將傳回**NULL**並將**errno**設定為**EINVAL**。

如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**fopen**函數將打開由*檔案名*指定的檔案。 預設情況下,使用 ANSI 代碼頁 (CP_ACP)解釋窄*的檔名*字串。 在 Windows 桌面應用程式中，這可以透過 [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) 函式變更為 OEM 字碼頁 (CP_OEMCP)。 您可以使用[AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi)函數來確定是否使用 ANSI 或系統預設 OEM 代碼頁解釋*檔名*。 **_wfopen**是一個寬字元版本的**fopen;** 要 **_wfopen**的參數是寬字元字串。 否則 **,_wfopen**和**開的**則相同。 只使用 **_wfopen**不會影響檔流中使用的編碼字元集。

**fopen**接受在執行時檔系統上有效的路徑;**fopen**接受涉及映射網路驅動器的 UNC 路徑和路徑,只要執行代碼的系統在執行時有權存取共享或映射驅動器。 建構**fopen**的路徑時,請確保驅動器、路徑或網路共用將在執行環境中可用。 您可以使用正斜線 (/) 或反斜線 (\\) 作為路徑中的目錄分隔符號。

務必檢查傳回值，在對檔案執行其他任何作業之前，查看指標是否為 NULL。 如果發生錯誤,將設置全域變數**errno,** 並可用於獲取特定的錯誤資訊。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="unicode-support"></a>Unicode 支援

**fopen**支援 Unicode 檔案流。 要打開 Unicode 檔,請傳遞一個**ccs**標誌,該標誌指定所需的編碼以**打開**,如下所示。

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=**_encoding_**");**

允許的*編碼*值是 UNICODE、UTF-8 和**UTF-16LE**。 **UNICODE** **UTF-8**

在 Unicode 模式下打開檔時,輸入函數會將從檔中讀取的數據轉換為作為**類型wchar_t**儲存的 UTF-16 資料。 寫入在 Unicode 模式開啟的檔案的函數需要包含 UTF-16 資料的緩衝區儲存為**型態wchar_t**。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試在 Unicode 模式下讀取或寫入奇數位節會導致[參數驗證](../../c-runtime-library/parameter-validation.md)錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。

如果檔案已經存在，而且已開啟來進行讀取或附加，則位元順序標記 (BOM) (如果已在檔案中) 會決定編碼方式。 BOM 編碼優先於**由 ccs**標誌指定的編碼。 僅當不存在 BOM 或檔是新檔時,才使用**ccs**編碼。

> [!NOTE]
> 物料清單檢測僅適用於在 Unicode 模式下打開的檔(即透過傳遞**ccs**標誌)。

下表總結了用於為檔中**的 fopen**和位元組順序標記提供的各種**ccs**標誌的模式。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>根據 ccs 旗標和 BOM 使用的編碼方式

|ccs 標誌|沒有 BOM (或新檔案)|BOM：UTF-8|BOM：UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

開啟以供在 Unicode 模式下寫入的檔案會有 BOM 自動寫入其中。

如果*模式*為 **"a,ccs_**_編碼_**"****",fopen**首先嘗試使用讀取和寫入存取打開檔。 如果這個動作成功，則函式會讀取 BOM 以判斷檔案的編碼方式，如果失敗，則函式會使用檔案的預設編碼方式。 在這兩種情況下 **,fopen**都將使用僅寫入訪問重新打開檔。 (這僅適用於 **"a"** 模式,不適用於 **"a+"** 模式。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

字串*模式*指定為檔案請求的存取類型,如下所示。

|*模式*|存取|
|-|-|
| **"r"** | 開啟以讀取。 如果檔案不存在或找不到,**則 fopen**呼叫將失敗。 |
| **"w"** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **"a"** | 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。 |
| **"r+"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w+"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a+"** | 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。 |

使用 **"a'** 存取類型或 **'a+'** 存取類型開啟檔時,所有寫入操作都發生在檔案的末尾。 可以使用[fseek](fseek-fseeki64.md)或[後退](rewind.md)重新定位檔指標,但在執行任何寫入操作之前,始終將其移回檔末尾。 因此，無法覆寫現有資料。

**"a'** 模式在追加到檔之前不會刪除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 在將 EOF 標記追加到檔之前 **,「a+」** 模式會刪除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 **"a+"** 模式是追加到使用 CTRL_Z EOF 標記終止的流檔所必需的。

指定 **"r+"、"w+"** 或 **"w+"****"a+"** 存取類型時,將啟用讀取和寫入(該檔表示為"更新"打開)。 不過，當您從讀取切換為寫入時，輸入作業一定會遇到 EOF 標記。 如果沒有 EOF，您就必須使用檔案定位函式的介入呼叫。 檔案定位功能是**fsetpos,fseek**與[fseek](fseek-fseeki64.md)[倒帶](rewind.md)。 當您從寫入切換到讀取時,必須使用中間調用來**fflush**或檔定位函數。

除了前面的值之外,還可以將以下字元追加到*模式*,以指定換行符的轉換模式。

|*模式*修改器|翻譯模式|
|-|-|
| **t** | 以文字 (已轉譯) 模式開啟。 |
| **B** | 在二進位(未翻譯)模式下打開;禁止使用涉及回車符和換行符的翻譯。 |

在文字模式下,CTRL_Z被解釋為輸入上的 EOF 字元。 在使用 **「a+」** 打開用於讀取/寫入的檔案中 **,fopen**會在檔案末尾檢查 CTRL_Z 並將其刪除(如果可能)。 這樣做是因為使用[fseek](fseek-fseeki64.md)和**ftell**在以 CTRL_Z 結尾的檔內移動可能會導致[fseek](fseek-fseeki64.md)在檔末尾附近操作不正確。

在文本模式下,在輸入時將回料返回行饋送組合轉換為單行饋送,在輸出時將換行符轉換為回饋列饋送組合。 Unicode 資料流 I/O 函式在文字模式 (預設) 下運作時，會假設來源或目的資料流是多位元組字元的序列。 因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 (就像呼叫 **mbtowc** 函式一樣)。 基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 (就像呼叫 **wctomb** 函式一樣)。

如果在*模式下*未給出**t**或**b,** 則預設轉換模式由全域變數[_fmode](../../c-runtime-library/fmode.md)定義。 如果**t**或**b**預置到參數,則函數會失敗並傳回**NULL**。

如需如何在 Unicode 及多位元組資料流 I/O 中使用文字與二進位模式的詳細資訊，請參閱 [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 及 [文字和二進位模式的 Unicode 資料流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

以下選項可以追加到*模式*以指定其他行為。

|*模式*修改器|行為|
|-|-|
| **C** | 啟用關聯*檔名*的提交標誌,以便在調用**fflush**或 **_flushall**時,檔緩衝區的內容直接寫入磁碟。 |
| **n** | 將關聯*檔名*的提交標誌重置為"不提交」。 這是預設值。 如果將程式與 COMMODE.OBJ 連結，也會覆寫全域認可旗標。 除非您明確連結程式與 COMMODE.OBJ，否則全域認可旗標的預設值為 "no-commit" (請參閱[連結選項](../../c-runtime-library/link-options.md))。 |
| **N** | 指定子處理序不繼承檔案。 |
| **S** | 指定針對但不限於磁碟的循序存取進行快取最佳化。 |
| **R** | 指定針對但不限於磁碟的隨機存取進行快取最佳化。 |
| **T** | 指定檔案做為暫存檔。 可能的話，不將其清除至磁碟。 |
| **D** | 指定檔案做為暫存檔。 當最後一個檔案指標關閉時，將其刪除。 |
| **ccs=**_encoding_ | 指定要用於此檔的編碼字元集 **(UTF-8、UTF-16LE**或**UNICODE****UTF-16LE**之一)。 如果您想要使用 ANSI 編碼方式，請保持為未指定。 |

**在 fopen**和 **_fdopen**中使用的*模式*字串的有效字元對應於[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)中使用的*滯後*參數,如下所示。

|*模式*字串的字元|\_開/\_開*的等效滯後*值|
|-------------------------------|----------------------------------------------------|
|**a**|**\_O\_WRONLY** &#124; ** \_\_O APPEND(** 通常**\_\_O WRONLY** &#124; ** \_O\_CREAT** &#124; ** \_O\_APPEND)**|
|**a+**|**\_O\_RDWR** &#124; ** \_ \_O APPEND(** 通常**\_\_O RDWR** &#124; ** \_O\_APPEND** &#124; ** \_O\_CREAT** )|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (通常**\_\_O WRONLY** &#124; ** \_ \_O CREAT** &#124; ** \_O\_TRUNC**)|
|**w***|**\_O\_RDWR** (通常**\_\_O RDWR** &#124; ** \_ \_O CREAT** &#124; ** \_O\_TRUNC**)|
|**B**|**\_O\_BINARY**|
|**t**|**\_O\_文字**|
|**C**|None|
|**n**|None|
|**S**|**\_O\_順序**|
|**R**|**\_O\_隨機**|
|**T**|**\_O\_肖特裡**|
|**D**|**\_O\_TEMPORARY**|
|**ccs=UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs=UTF-16LE**|**\_O\_UTF16**|

如果使用**rb**模式,則不必移植代碼,並且如果您希望讀取大部分大型檔或不關心網路性能,也可以考慮是否使用記憶體映射的 Win32 檔作為選項。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> 或 \<wchar.h>|

**_wfopen**是微軟的擴展。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**D** **n** **t** **S** **R** **T****fopen****_fdopen**c、n、t、S、R、T 和 D 模式選項是 Microsoft 用於 fopen 和 _fdopen 的擴展,不應在需要 ANSI 可移植性的情況下使用。 *mode* ** **

## <a name="example-1"></a>範例 1

下列程式會開啟兩個檔案。  它使用**fclose**關閉第一個檔 **,_fcloseall**關閉所有剩餘的檔。

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
