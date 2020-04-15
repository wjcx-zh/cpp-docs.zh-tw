---
title: fopen_s、_wfopen_s
ms.date: 4/2/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
ms.openlocfilehash: 80d04e75637cfab9795bf5dfb9da9786cf4ebd71
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346485"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s、_wfopen_s

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

*檔案名稱*<br/>
檔案名稱。

*模式*<br/>
允許的存取類型。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。 如需這些傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*pFile*|*檔案名稱*|*模式*|傳回值|*pFile*的內容|
|-------------|----------------|------------|------------------|------------------------|
|**空**|任意|任意|**埃因瓦爾**|未變更|
|任意|**空**|任意|**埃因瓦爾**|未變更|
|任意|任意|**空**|**埃因瓦爾**|未變更|

## <a name="remarks"></a>備註

**由fopen_s**和 **_wfopen_s**打開的檔不可共用。 如果需要檔是可共用的,請使用[_fsopen,使用](fsopen-wfsopen.md)具有相應共用模式常量_wfsopen,例如 **,_SH_DENYNO**讀取/寫入共用。

**fopen_s**函數將打開由*檔案名*指定的檔案。 **_wfopen_s**是**fopen_s**的寬字元版本;要 **_wfopen_s**的參數是寬字元字串。 **_wfopen_s**和**fopen_s**行為相同。

**fopen_s**接受在執行時文件系統上有效的路徑;FOPEN_S接受涉及映射網路驅動器的 UNC 路徑和路徑 **,只要執行**代碼的系統在執行時可以存取共享或映射的網路驅動器。 建構**fopen_s**路徑時,不要對執行環境中的驅動器、路徑或網路共享的可用性進行假設。 您可以使用正斜線 (/) 或反斜線 (\\) 作為路徑中的目錄分隔符號。

這些函式會驗證它們的參數。 如果*pFile、**檔名*或*模式*是空指標,則這些函數將生成無效的參數異常,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

請務必檢查傳回值，在對檔案執行任何進一步作業之前，查看此函式是否已成功。 如果發生錯誤,將返回錯誤代碼並設置全域變數**errno。** 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="unicode-support"></a>Unicode 支援

**fopen_s**支援 Unicode 檔流。 要開啟新的或現有的 Unicode 檔,請傳遞一個*ccs*標誌,該旗標指定所需的編碼**以fopen_s**:

**fopen_s(&fp, "newfile.txt", "rw, ccs=**_encoding_**");**

允許的*編碼*值是 UNICODE、UTF-8 和**UTF-16LE**。 **UNICODE** **UTF-8** 如果沒有為*編碼*指定值 **,fopen_s**使用 ANSI 編碼。

如果檔案已經存在，而且已開啟來進行讀取或附加，則位元順序標記 (BOM) (如果已在檔案中) 會決定編碼方式。 BOM 編碼優先於*由 ccs*標誌指定的編碼。 僅當不存在 BOM 或檔是新檔時,才使用*ccs*編碼。

> [!NOTE]
> 物料清單檢測僅適用於在 Unicode 模式下打開的檔;也就是說,通過傳遞*ccs*標誌。

下表總結了為**fopen_s**和檔中的位元組訂單標記提供的各種*ccs*標誌的模式。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>根據 ccs 旗標和 BOM 使用的編碼方式

|ccs 標誌|沒有 BOM (或新檔案)|BOM：UTF-8|BOM：UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

開啟以供在 Unicode 模式下寫入的檔案會有 BOM 自動寫入其中。

如果*模式*為 **"a,ccs_**_編碼_**",fopen_s**首先嘗試打開具有讀取存取和寫**fopen_s**入存取許可權的檔。 如果成功，則函式會讀取 BOM 以判斷檔案的編碼方式，如果不成功，則函式會使用檔案的預設編碼方式。 在這兩種情況下 **,fopen_s**然後重新打開具有僅寫入存取許可權的檔。 (這僅適用於**模式,** 不適用於 **.)**

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

字串*模式*指定為檔案請求的存取類型,如下所示。

|*模式*|存取|
|-|-|
| **"r"** | 開啟以讀取。 如果檔不存在或找不到,則**fopen_s**調用失敗。 |
| **"w"** | 開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。 |
| **"a"** | 開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。 如果檔案不存在時，建立檔案。 |
| **"r+"** | 開啟以進行讀取和寫入。 檔案必須存在。 |
| **"w+"** | 開啟空白檔案以進行讀取和寫入。 如果檔案存在，其內容會遭到銷毀。 |
| **"a+"** | 開啟以進行讀取和附加。 附加作業包括在將新資料寫入檔案之前移除 EOF 標記。 寫入完成後，不會還原 EOF 標記。 如果檔案不存在時，建立檔案。 |

使用 **"a'** 或 **"a+"** 存取類型打開檔時,所有寫入操作都發生在檔的末尾。 可以使用[fseek](fseek-fseeki64.md)或[後退](rewind.md)重新定位檔指標,但在執行任何寫入操作之前,該檔指標始終移回檔末尾,以便無法覆蓋現有數據。

在追加到檔案之前 **,"a"** 模式不會刪除 EOF 標記。 進行附加之後，MS-DOS TYPE 命令只顯示到原始 EOF 標記為止的資料，任何附加至檔案的資料都不會出現。 **"a+"** 模式在追加到檔之前確實會刪除 EOF 標記。 附加之後，MS-DOS TYPE 命令會顯示檔案中的所有資料。 使用 CTRL_Z EOF 標記終止的流檔需要 **'a+'** 模式。

指定 **"r+"、"w+"** 或 **"w+"****"a+"** 存取類型時,允許讀取和寫入。 (該檔表示為"更新"打開。但是,當您從讀取切換到寫入時,輸入操作必須遇到 EOF 標記。 如果沒有 EOF，您就必須使用檔案定位函式的介入呼叫。 檔案定位函數是**fsetpos、fseek**和[fseek](fseek-fseeki64.md)[倒帶](rewind.md)。 當您從寫入切換到讀取時,必須使用中間調用來**fflush**或檔定位函數。

除上述值外,還可以在*模式下*包含以下字元,以指定換行元的轉換模式:

|*模式*修改器|翻譯模式|
|-|-|
| **t** | 以文字 (已轉譯) 模式開啟。 |
| **B** | 在二進位(未翻譯)模式下打開;禁止使用涉及回車符和換行符的翻譯。 |

在文字(翻譯)模式下,CTRL_Z 被解釋為輸入時的檔結尾字元。 在打開用於讀取/寫入 **「a+」** 的檔案中 **,fopen_s**檢查檔末尾的 CTRL_Z,並盡可能將其刪除。 這樣做是因為使用[fseek](fseek-fseeki64.md)和**ftell**在以 CTRL_Z 結尾的檔內移動,可能會導致[fseek](fseek-fseeki64.md)在檔末尾附近行為不當。

此外,在文本模式下,在輸入時將回料返回行饋送組合轉換為單行饋送,在輸出時將換行符轉換為回車換行換行組合。 Unicode 資料流 I/O 函式在文字模式 (預設) 下運作時，會假設來源或目的資料流是多位元組字元的序列。 因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 (就像呼叫 **mbtowc** 函式一樣)。 基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 (就像呼叫 **wctomb** 函式一樣)。

如果在*模式下*未給出**t**或**b,** 則預設轉換模式由全域變數[_fmode](../../c-runtime-library/fmode.md)定義。 如果**t**或**b**預置到參數,則函數會失敗並傳回**NULL**。

如需在 Unicode 和多位元組資料流 I/O 中使用文字和二進位模式的詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文字和二進位模式的 Unicode 資料流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

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

**fopen_s**和[_fdopen](fdopen-wfdopen.md)中使用的*模式*字串的有效字元對應於[_open](open-wopen.md)和[_sopen](sopen-wsopen.md)中使用的*滯後*參數,如下所示。

|*模式*字串的字元|_open/_sopen*的滯後*值等值|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** **_O_WRONLY&#124;_O_APPEND(****_O_WRONLY**通常 _O_WRONLY&#124;_O_CREAT&#124;*_O_APPEND*) **_O_CREAT**|
|**a+**|**_O_RDWR** &#124; **_O_APPEND** (usually **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**R**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**w**|**_O_WRONLY(****_O_WRONLY**通常 **_O_WRONLY&#124;_O_CREAT&#124;*** _O_TRUNC])|
|**w***|**_O_RDWR** (usually **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**B**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**C**|None|
|**n**|None|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

如果您使用的是**rb**模式,則不需要移植代碼,並且希望讀取大量檔和/或不關心網路性能,則記憶體映射的 Win32 檔可能也是一個選項。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

**c、n**和**t** *模式*選項是 Microsoft **fopen_s**和[_fdopen](fdopen-wfdopen.md)的擴展,在需要 ANSI 可移植性的情況下不應使用。 **n**

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
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
