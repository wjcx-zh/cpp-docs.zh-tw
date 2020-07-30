---
title: _open、_wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wopen
- _topen
- _open
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
ms.openlocfilehash: f57ad33fe09938e0f04d0ca2615898fa2cdbd642
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226199"
---
# <a name="_open-_wopen"></a>_open、_wopen

開啟檔案。 這些函式已遭取代，因為已經有更安全的版本，請參閱 [_sopen_s、_wsopen_s](sopen-s-wsopen-s.md)。

## <a name="syntax"></a>語法

```C
int _open(
   const char *filename,
   int oflag [,
   int pmode]
);
int _wopen(
   const wchar_t *filename,
   int oflag [,
   int pmode]
);
```

### <a name="parameters"></a>參數

*filename*<br/>
檔案名稱

*oflag*<br/>
允許的作業種類。

*pmode*<br/>
權限模式。

## <a name="return-value"></a>傳回值

這些函式每一個都會傳回已開啟檔案的檔案描述項。 傳回值-1 表示發生錯誤;在此情況下， **errno**會設定為下列其中一個值。

|errno 值|條件|
|-|-|
| **EACCES** | 嘗試開啟唯讀檔案以供寫入，檔案的共用模式不允許指定的作業，或是指定的路徑為目錄。 |
| **EEXIST** | 已指定 **_O_CREAT**和 **_O_EXCL**旗標，但是*filename*已經存在。 |
| **EINVAL** | 不正確*oflag*或*pmode*引數。 |
| **EMFILE** | 沒有更多檔案描述項可用 (開啟了太多檔案)。 |
| **ENOENT** | 找不到檔案或路徑。 |

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Open**函式會開啟*filename*所指定的檔案，並準備它以供讀取或寫入（如*oflag*所指定）。 **_wopen**是寬字元版本的 **_open**;**_wopen**的*filename*引數是寬字元字串。 相反地， **_wopen**和 **_open**的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*oflag*是整數運算式，由下列一或多個資訊清單常數或常陣列合所組成，其定義于中 \<fcntl.h> 。

|*oflag*常數|行為|
|-|-|
| **_O_APPEND** | 在每次寫入作業之前，將檔案指標移到檔案的結尾。 |
| **_O_BINARY** | 以二進位 (未轉譯) 模式開啟檔案 (如需二進位模式的說明，請參閱 [fopen](fopen-wfopen.md))。 |
| **_O_CREAT** | 建立檔案並開啟以供寫入。 若*filename*指定的檔案存在，則不會有任何作用。 當指定 **_O_CREAT**時， *pmode*引數是必要的。 |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | 將檔案建立為暫存檔，若有可能的話，請勿清除至磁碟。 當指定 **_O_CREAT**時， *pmode*引數是必要的。 |
| **_O_CREAT** &#124; **_O_TEMPORARY** | 將檔案建立為暫存檔；當最後一個檔案描述項關閉時會刪除檔案。 當指定 **_O_CREAT**時， *pmode*引數是必要的。 |
| **_O_CREAT** &#124;`_O_EXCL` | 如果*filename*指定的檔案存在，則會傳回錯誤值。 僅適用于與 **_O_CREAT**搭配使用時。 |
| **_O_NOINHERIT** | 防止建立共用檔案描述項。 |
| **_O_RANDOM** | 指定針對但不限於磁碟的隨機存取進行快取最佳化。 |
| **_O_RDONLY** | 開啟檔案為僅供讀取。 不能以 **_O_RDWR**或 **_O_WRONLY**指定。 |
| **_O_RDWR** | 開啟檔案以進行讀取和寫入。 不能以 **_O_RDONLY**或 **_O_WRONLY**指定。 |
| **_O_SEQUENTIAL** | 指定針對但不限於磁碟的循序存取進行快取最佳化。 |
| **_O_TEXT** | 以文字 (已轉譯) 模式開啟檔案 (如需詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](fopen-wfopen.md))。 |
| **_O_TRUNC** | 開啟檔案，並將檔案截斷為零長度；檔案必須具有寫入權限。 不能與 **_O_RDONLY**一起指定。 搭配 **_O_CREAT**使用的 **_O_TRUNC**會開啟現有檔案或建立檔案。 **注意：****_O_TRUNC**旗標會終結指定檔案的內容。 |
| **_O_WRONLY** | 將檔案開啟為僅供寫入。 不能以 **_O_RDONLY**或 **_O_RDWR**指定。 |
| **_O_U16TEXT** | 以 Unicode UTF-16 模式開啟檔案。 |
| **_O_U8TEXT** | 以 Unicode UTF-8 模式開啟檔案。 |
| **_O_WTEXT** | 以 Unicode 模式開啟檔案。 |

若要指定檔案存取模式，您必須指定 [ **_O_RDONLY**]、[ **_O_RDWR**] 或 [ **_O_WRONLY**]。 存取模式沒有預設值。

如果 **_O_WTEXT**用來開啟檔案以供讀取， **_open**會讀取檔案的開頭，並檢查位元組順序標記（BOM）。 若有 BOM，會將檔案視為 UTF-8 或 UTF-16LE，這會取決於 BOM。 若無 BOM，會將檔案視為 ANSI。 使用 **_O_WTEXT**開啟檔案以進行寫入時，會使用 utf-16。 不論先前的設定或位元組順序標記為何，如果使用 **_O_U8TEXT** ，檔案一律會以 utf-8 開啟;如果使用 **_O_U16TEXT** ，檔案一律會以 utf-16 的形式開啟。

使用 **_O_WTEXT**、 **_O_U8TEXT**或 **_O_U16TEXT**以 Unicode 模式開啟檔案時，輸入函式會將從檔案讀取的資料，轉譯為儲存為類型的 utf-16 資料 **`wchar_t`** 。 寫入以 Unicode 模式開啟之檔案的函式，會預期包含儲存為類型之 UTF-16 資料的緩衝區 **`wchar_t`** 。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元組會導致參數驗證錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。

如果 **_open**以 **_O_WRONLY**  |  **_O_APPEND** （附加模式）和 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**呼叫 _open，它會先嘗試開啟檔案以進行讀取和寫入、讀取 BOM，然後重新開啟以供寫入。 若開啟檔案以供讀取和寫入失敗，則會僅針對寫入開啟檔案，並使用 Unicode 模式設定的預設值。

當兩個或多個資訊清單常數用來形成*oflag*引數時，常數會與位 or 運算子（ **&#124;** ）結合。 如需二進位及文字模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

只有在指定 **_O_CREAT**時，才需要*pmode*引數。 如果檔案已經存在，則會忽略*pmode* 。 否則， *pmode*會指定檔案許可權設定，這會在第一次關閉新檔案時設定。 **_open**在設定許可權之前，將目前的檔案許可權遮罩套用至*pmode* 。 （如需詳細資訊，請參閱[_umask](umask.md)）。*pmode*是一個整數運算式，其中包含下列定義的其中一個或兩個資訊清單常數 \<sys\stat.h> 。

|*pmode*|意義|
|-|-|
| **_S_IREAD** | 只允許讀取。 |
| **_S_IWRITE** | 允許寫入。 (實際上允許讀取和寫入)。 |
| **_S_IREAD** &#124; **_S_IWRITE** | 允許讀取和寫入。 |

當同時指定兩個常數時，會使用位 OR 運算子（ **&#124;** ）聯結。 在 Windows 所有檔案皆為可讀取；不提供僅限寫入的權限。 因此， **_S_IWRITE**和 **_S_IREAD**  |  **_S_IWRITE**的模式是相等的。

如果 **_S_IREAD**和 **_S_IWRITE**的某種組合的值指定為*pmode*，即使它會在另一個作業系統中指定有效的*pmode* ，或是指定了允許的*oflag*值以外的任何值，函式也會在 Debug 模式中產生判斷提示，並叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回-1，並將**errno**設定為**EINVAL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<io.h> 或 \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_open**和 **_wopen**是 Microsoft 擴充功能。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_open.c
// compile with: /W3
/* This program uses _open to open a file
* named CRT_OPEN.C for input and a file named CRT_OPEN.OUT
* for output. The files are then closed.
*/
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int fh1, fh2;

   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996
   // Note: _open is deprecated; consider using _sopen_s instead
   if( fh1 == -1 )
      perror( "Open failed on input file" );
   else
   {
      printf( "Open succeeded on input file\n" );
      _close( fh1 );
   }

   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |
                            _S_IWRITE ); // C4996
   if( fh2 == -1 )
      perror( "Open failed on output file" );
   else
   {
      printf( "Open succeeded on output file\n" );
      _close( fh2 );
   }
}
```

### <a name="output"></a>輸出

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>另請參閱

[低層級 i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
