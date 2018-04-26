---
title: _open、_wopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _open
- _wopen
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
- _wopen
- _topen
- _open
dev_langs:
- C++
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
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4b25e263d9483f308161a823b136643e1451106
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="open-wopen"></a>_open、_wopen

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
允許的作業類型。

*pmode*<br/>
權限模式。

## <a name="return-value"></a>傳回值

這些函式每一個都會傳回已開啟檔案的檔案描述項。 傳回值-1 表示錯誤。在此情況下**errno**設為下列值之一。

|errno 值|條件|
|-|-|
**EACCES**|嘗試開啟唯讀檔案以供寫入，檔案的共用模式不允許指定的作業，或是指定的路徑為目錄。
**EEXIST**|**_O_CREAT**和 **_O_EXCL**旗標指定，但*filename*已經存在。
**EINVAL**|無效*oflag*或*pmode*引數。
**EMFILE**|沒有更多檔案描述項可用 (開啟了太多檔案)。
**ENOENT**|找不到檔案或路徑。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Open**函式會開啟所指定的檔案*filename*並準備好供讀取或寫入，所指定*oflag*。 **_wopen**是寬字元版本的 **_open**; *filename*引數 **_wopen**是寬字元字串。 **_wopen**和 **_open**除此之外的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*oflag*整數運算式形成從其中一個或多個下列資訊清單常數或常數組合，定義於\<.h >。

|*oflag*常數|行為|
|-|-|
**_O_APPEND**|在每次寫入作業之前，將檔案指標移到檔案的結尾。
**_O_BINARY**|以二進位 (未轉譯) 模式開啟檔案 (如需二進位模式的描述，請參閱 [fopen](fopen-wfopen.md))。
**_O_CREAT**|建立檔案並開啟以供寫入。 如果指定的檔案有任何作用*filename*存在。 *Pmode*引數時，需要 **_O_CREAT**指定。
**_O_CREAT** &AMP;#124; **_O_SHORT_LIVED**|將檔案建立為暫存檔，若有可能的話，請勿清除至磁碟。 *Pmode*引數時，需要 **_O_CREAT**指定。
**_O_CREAT** &AMP;#124; **_O_TEMPORARY**|將檔案建立為暫存檔；當最後一個檔案描述項關閉時會刪除檔案。 *Pmode*引數時，需要 **_O_CREAT**指定。
**_O_CREAT**&AMP;#124; ` _O_EXCL`|如果指定的檔案傳回錯誤值*filename*存在。 只有在搭配使用時，才適用 **_O_CREAT**。
**_O_NOINHERIT**|防止建立共用檔案描述項。
**_O_RANDOM**|指定針對但不限於磁碟的隨機存取進行快取最佳化。
**_O_RDONLY**|開啟檔案為僅供讀取。 不能與指定 **_O_RDWR**或 **_O_WRONLY**。
**_O_RDWR**|開啟檔案以進行讀取和寫入。 不能與指定 **_O_RDONLY**或 **_O_WRONLY**。
**_O_SEQUENTIAL**|指定針對但不限於磁碟的循序存取進行快取最佳化。
**_O_TEXT**|以文字 (已轉譯) 模式開啟檔案 (如需詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](fopen-wfopen.md))。
**_O_TRUNC**|開啟檔案，並將檔案截斷為零長度；檔案必須具有寫入權限。 不能與指定 **_O_RDONLY**。 **_O_TRUNC**搭配 **_O_CREAT**開啟現有的檔案，或建立檔案。 **注意：** **_O_TRUNC**旗標會終結指定檔案的內容。
**_O_WRONLY**|將檔案開啟為僅供寫入。 不能與指定 **_O_RDONLY**或 **_O_RDWR**。
**_O_U16TEXT**|以 Unicode UTF-16 模式開啟檔案。
**_O_U8TEXT**|以 Unicode UTF-8 模式開啟檔案。
**_O_WTEXT**|以 Unicode 模式開啟檔案。

若要指定檔案存取模式，您必須指定 **_O_RDONLY**， **_O_RDWR**，或 **_O_WRONLY**。 存取模式沒有預設值。

如果 **_O_WTEXT**用來開啟檔案進行讀取， **_open**讀取檔案開頭，並檢查是否有位元組順序標示 (BOM)。 若有 BOM，會將檔案視為 UTF-8 或 UTF-16LE，這會取決於 BOM。 若無 BOM，會將檔案視為 ANSI。 當開啟檔案進行寫入使用 **_O_WTEXT**，會使用 utf-16。 不論任何先前的設定或位元順序標記為何，如果 **_O_U8TEXT**是使用，一律將檔案開啟為 utf-8; 如果 **_O_U16TEXT**是使用，一律將檔案開啟為 utf-16。

以 Unicode 模式開啟檔案是時，使用 **_O_WTEXT**， **_O_U8TEXT**，或 **_O_U16TEXT**，請輸入函式轉譯成 utf-16 資料從檔案讀取資料儲存為類型**wchar_t**。 寫入至以 Unicode 模式開啟檔案的函式預期會包含儲存為類型的 utf-16 資料的緩衝區**wchar_t**。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元組會導致參數驗證錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。

如果 **_open**呼叫 **_O_WRONLY** | **_O_APPEND** （附加模式） 和 **_O_WTEXT**， **_O_U16TEXT**，或 **_O_U8TEXT**，它會先嘗試開啟檔案進行讀取和寫入，讀取 BOM，然後重新開啟它僅供寫入。 若開啟檔案以供讀取和寫入失敗，則會僅針對寫入開啟檔案，並使用 Unicode 模式設定的預設值。

當兩個或多個資訊清單常數用於表單*oflag*引數，會使用位元 OR 運算子結合常數 ( **&#124;** )。 如需二進位及文字模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

*Pmode*引數是需要時才 **_O_CREAT**指定。 如果檔案已經存在， *pmode*會被忽略。 否則， *pmode*指定檔案的權限設定，新檔案第一次關閉時會進行此設定。 **_open**目前檔案權限遮罩套用至*pmode*之前已設定權限。 (如需詳細資訊，請參閱[_umask](umask.md)。)*pmode*是整數運算式，其中包含一或兩個下列的資訊清單常數，定義於\<sys\stat.h >。

|*pmode*|意義|
|-|-|
**_S_IREAD**|只允許讀取。
**_S_IWRITE**|允許寫入 (實際上允許讀取和寫入)。
**_S_IREAD** &AMP;#124; **_S_IWRITE**|允許讀取和寫入。

當兩個常數時，其是否加入位元 OR 運算子 ( **&#124;** )。 在 Windows 所有檔案皆為可讀取；不提供僅限寫入的權限。 因此，模式 **_S_IWRITE**和 **_S_IREAD** | **_S_IWRITE**相等。

如果值以外的某種組合 **_S_IREAD**和 **_S_IWRITE**指定*pmode*— 即使會指定有效的*pmode*在其他作業系統，或任何值而不是允許*oflag*指定值，函式在偵錯模式產生判斷提示，並叫用無效參數處理常式，中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回-1 以及設定執行**errno**至**EINVAL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|
|**_wopen**|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|

**_open**和 **_wopen**是 Microsoft 擴充功能。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[dup、dup2](dup-dup2.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
