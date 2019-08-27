---
title: fopen_s、_wfopen_s
ms.date: 11/04/2016
apiname:
- _wfopen_s
- fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
ms.openlocfilehash: e4ccce3c4a4fe1e327b7830ef03f6ab69f2d7814
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376211"
---
# <a name="fopens-wfopens"></a>fopen_s、_wfopen_s

開啟檔案。 這些版本的 [fopen、_wfopen](fopen-wfopen.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*pFile*<br/>
指向檔案指標 (將接收指向已開啟檔案之指標) 的指標。

*filename*<br/>
檔案名稱。

*mode*<br/>
允許的存取類型。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。 如需這些傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*pFile*|*filename*|*mode*|傳回值|*PFile*的內容|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|any|any|**EINVAL**|未變更|
|any|**NULL**|any|**EINVAL**|未變更|
|any|any|**NULL**|**EINVAL**|未變更|

## <a name="remarks"></a>備註

**Fopen_s**和 **_wfopen_s**所開啟的檔案無法共用。 如果您需要可共用的檔案, 請使用[_fsopen、_wfsopen](fsopen-wfsopen.md)搭配適當的共用模式常數, 例如, **_SH_DENYNO**進行讀取/寫入共用。

**Fopen_s**函數會開啟*filename*所指定的檔案。 **_wfopen_s**是寬字元版本的**fopen_s**; **_wfopen_s**的引數是寬字元字串。 相反地, **_wfopen_s**和**fopen_s**的行為相同。

在執行時, **fopen_s**會接受在檔案系統上有效的路徑;只要執行程式碼的系統在執行時有權存取共用或對應的網路磁碟機機, **fopen_s**就會接受包含對應網路磁碟機機的 UNC 路徑和路徑。 當您為**fopen_s**建立路徑時, 請不要對執行環境中的磁片磁碟機、路徑或網路共用的可用性進行假設。 您可以使用正斜線 (/) 或反斜線 (\\) 作為路徑中的目錄分隔符號。

這些函式會驗證它們的參數。 如果*pFile*、 *filename*或*mode*是 null 指標, 則這些函式會產生無效參數例外狀況, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

請務必檢查傳回值，在對檔案執行任何進一步作業之前，查看此函式是否已成功。 如果發生錯誤, 則會傳回錯誤代碼並設定全域變數**errno** 。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="unicode-support"></a>Unicode 支援

**fopen_s**支援 Unicode 檔案資料流程。 若要開啟新的或現有的 Unicode 檔案, 請將指定所需編碼方式的*ccs*旗標傳遞至**fopen_s**:

**fopen_s(&fp, "newfile.txt", "rw, ccs=** _encoding_ **");**

允許的*編碼*值為**UNICODE**、 **utf-8**和**utf-16le**。 如果沒有指定*編碼*的值, **FOPEN_S**會使用 ANSI 編碼。

如果檔案已經存在，而且已開啟來進行讀取或附加，則位元順序標記 (BOM) (如果已在檔案中) 會決定編碼方式。 BOM 編碼優先于*ccs*旗標所指定的編碼方式。 只有當 BOM 不存在或檔案為新檔案時, 才會使用*ccs*編碼。

> [!NOTE]
> BOM 偵測只適用于以 Unicode 模式開啟的檔案;也就是說, 藉由傳遞*ccs*旗標。

下表摘要說明提供給**fopen_s**的各種*ccs*旗標模式, 以及檔案中的位元組順序標記。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>根據 ccs 旗標和 BOM 使用的編碼方式

|ccs 旗標|沒有 BOM (或新檔案)|BOMUTF-8|BOMUTF-16|
|----------------|----------------------------|-----------------|------------------|
|**消除**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

開啟以供在 Unicode 模式下寫入的檔案會有 BOM 自動寫入其中。

如果*mode*是 **"a, ccs =** _encoding_ **"** , **fopen_s**會先嘗試使用讀取權限和寫入存取來開啟檔案。 如果成功，則函式會讀取 BOM 以判斷檔案的編碼方式，如果不成功，則函式會使用檔案的預設編碼方式。 不論是哪一種情況, **fopen_s**都會以僅限寫入的存取權來重新開啟檔案。 (這只適用  于模式, 而不**是 +** )。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

字元字串*模式*會指定針對檔案要求的存取類型, 如下所示。

|*mode*|Access|
|-|-|
| **"r"** | 開啟以讀取。 如果檔案不存在或找不到, **fopen_s**呼叫將會失敗。 |
| **"w"** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **"a"** | 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。 |
| **"r+"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w+"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a+"** | 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。 |

使用 **"a"** 或 **"a +"** 存取類型開啟檔案時, 所有寫入作業都會在檔案結尾進行。 您可以使用[fseek](fseek-fseeki64.md)或倒轉來重新置放檔案[](rewind.md)指標, 但是在執行任何寫入作業之前, 一律會移回至檔案結尾, 因此無法覆寫現有資料。

在附加到檔案之前, **"a"** 模式不會移除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 **"A +"** 模式會先移除 EOF 標記, 再將附加至檔案。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 附加至使用 CTRL + Z EOF 標記終止的資料流程檔案時, 需要 **"a +"** 模式。

指定 **"r +"** 、 **"w +"** 或 **"a +"** 存取類型時, 同時允許讀取和寫入。 (表示檔案是要開啟以供「更新」之用。)不過，當您從讀取切換為寫入時，輸入作業一定會遇到 EOF 標記。 如果沒有 EOF，您就必須使用檔案定位函式的介入呼叫。 檔案定位函式為**fsetpos**、 [fseek](fseek-fseeki64.md)和倒轉。 [](rewind.md) 當您從寫入切換為讀取時, 您必須使用**fflush**的中間呼叫或檔案定位函式。

除了上述的值之外, 您還可以在*模式*中包含下列字元, 以指定分行符號的轉譯模式:

|*模式*修飾詞|轉譯模式|
|-|-|
| **t** | 以文字 (已轉譯) 模式開啟。 |
| **b** | 以二進位 (未轉譯) 模式開啟;會隱藏涉及回車和換行字元的翻譯。 |

在 [文字 (已轉譯)] 模式中, CTRL + Z 會在輸入時被視為檔案結尾字元。 在以 **"a +"** 開啟以進行讀取/寫入的檔案中, **fopen_s**會在檔案結尾檢查是否有 CTRL + Z, 並盡可能移除該檔案。 這是因為使用[fseek](fseek-fseeki64.md)和**FTELL**在以 CTRL + Z 結尾的檔案內移動, 可能會導致[fseek](fseek-fseeki64.md)在檔案結尾附近的行為不正確。

此外, 在文字模式中, 在輸入時, 會將換行字元組合轉譯成單行饋送, 而換行字元會轉譯為輸出上的換行分行符號組合。 Unicode 資料流 I/O 函式在文字模式 (預設) 下運作時，會假設來源或目的資料流是多位元組字元的序列。 因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 (就像呼叫 **mbtowc** 函式一樣)。 基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 (就像呼叫 **wctomb** 函式一樣)。

如果未在*模式*中指定**t**或**b** , 則預設轉譯模式是由全域變數[_fmode](../../c-runtime-library/fmode.md)所定義。 如果**t**或**b**前面加上引數, 則函式會失敗並傳回**Null**。

如需在 Unicode 和多位元組資料流 I/O 中使用文字和二進位模式的詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文字和二進位模式的 Unicode 資料流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

|*模式*修飾詞|行為|
|-|-|
| **C** | 啟用相關聯*檔案名*的認可旗標, 以便在呼叫**fflush**或 **_flushall**時, 將檔案緩衝區的內容直接寫入磁片。 |
| **n** | 將相關聯*檔案名*的認可旗標重設為「未認可」。 這是預設值。 如果將程式與 COMMODE.OBJ 連結，也會覆寫全域認可旗標。 除非您明確連結程式與 COMMODE.OBJ，否則全域認可旗標的預設值為 "no-commit" (請參閱 [Link Options](../../c-runtime-library/link-options.md))。 |
| **N** | 指定子處理序不繼承檔案。 |
| **S** | 指定針對但不限於磁碟的循序存取進行快取最佳化。 |
| **R** | 指定針對但不限於磁碟的隨機存取進行快取最佳化。 |
| **T** | 指定檔案做為暫存檔。 可能的話，不將其清除至磁碟。 |
| **D** | 指定檔案做為暫存檔。 當最後一個檔案指標關閉時，將其刪除。 |
| **ccs=** _encoding_ | 指定這個檔案要使用的編碼字元集 ( **utf-8**、 **Utf utf-16le**或**UNICODE**的其中一個)。 如果您想要使用 ANSI 編碼方式，請保持為未指定。 |

**Fopen_s**和[_fdopen](fdopen-wfdopen.md)中所使用之*模式*字串的有效字元會對應到[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)中使用的*oflag*引數, 如下所示。

|*模式*字串中的字元|_Open/_sopen 的對等*oflag*值|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY**&#124; **_O_APPEND** (通常是 **_O_WRONLY** &#124; **_O_CREAT** &#124;* * _O_APPEND * *)|
|**a+**|**_O_RDWR** &#124; **_O_APPEND** (usually **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**w**|**_O_WRONLY**(通常是 **_O_WRONLY** &#124; **_O_CREAT** &#124;* * _O_TRUNC * *)|
|**w+**|**_O_RDWR** (usually **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**C**|無|
|**n**|無|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

如果您使用的是**rb**模式, 則不需要移植您的程式碼, 而且預期會讀取很多檔案和 (或) 不在意網路效能, 而對應 Win32 檔案的記憶體也可能是一個選項。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

[ **C**]、[ **n**] 和 [ **t** *] 模式*選項是適用于**fopen_s**和[_fdopen](fdopen-wfdopen.md)的 Microsoft 擴充功能, 不應在需要 ANSI 可攜性的情況下使用。

## <a name="example"></a>範例

```C
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

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
f[reopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
