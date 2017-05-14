---
title: "_open、_wopen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 82b12ebfbff06c19a863bec7d8be2e6677c0148e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="open-wopen"></a>_open、_wopen
開啟檔案。 這些函式已遭取代，因為已經有更安全的版本，請參閱 [_sopen_s、_wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `filename`  
 檔案名稱  
  
 `oflag`  
 允許的作業類型。  
  
 `pmode`  
 權限模式。  
  
## <a name="return-value"></a>傳回值  
 這些函式每一個都會傳回已開啟檔案的檔案描述項。 傳回的值為 -1 表示錯誤，此情況中 `errno` 會設為下列值之一。  
  
 `EACCES`  
 嘗試開啟唯讀檔案以供寫入，檔案的共用模式不允許指定的作業，或是指定的路徑為目錄。  
  
 `EEXIST`  
指定了  `_O_CREAT` 和 `_O_EXCL` 旗標，但 `filename` 已存在。  
  
 `EINVAL`  
 無效的 `oflag` 或 `pmode` 引數。  
  
 `EMFILE`  
 沒有更多檔案描述項可用 (開啟了太多檔案)。  
  
 `ENOENT`  
 找不到檔案或路徑。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_open` 函式會開啟 `filename` 指定的檔案，並準備檔案，以供讀取或寫入 (由 `oflag` 指定)。 `_wopen` 是寬字元版本的 `_open`，`filename` 的 `_wopen` 引數是寬字元字串。 否則，`_wopen` 和 `_open` 的行為即會相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_topen`|`_open`|`_open`|`_wopen`|  
  
 `oflag` 是整數運算式，由一或多個下列資訊清單常數或常數組合所組成，且會定義於 \<fcntl.h> 中。  
  
 `_O_APPEND`  
 在每次寫入作業之前，將檔案指標移到檔案的結尾。  
  
 `_O_BINARY`  
 以二進位 (未轉譯) 模式開啟檔案 (如需二進位模式的說明，請參閱 [fopen](../../c-runtime-library/reference/fopen-wfopen.md))。  
  
 `_O_CREAT`  
 建立檔案並開啟以供寫入。 若 `filename` 指定的檔案存在則無影響。 指定 `pmode` 時，需要 `_O_CREAT` 引數。  
  
 `_O_CREAT` &#124; `_O_SHORT_LIVED`  
 將檔案建立為暫存檔，若有可能的話，請勿清除至磁碟。 指定 `pmode` 時，需要 `_O_CREAT` 引數。  
  
 `_O_CREAT` &#124; `_O_TEMPORARY`  
 將檔案建立為暫存檔；當最後一個檔案描述項關閉時會刪除檔案。 指定 `pmode` 時，需要 `_O_CREAT` 引數。  
  
 `_O_CREAT` &#124; `_O_EXCL`  
 若 `filename` 指定的檔案存在，會傳回錯誤值。 搭配 `_O_CREAT` 使用時才套用。  
  
 `_O_NOINHERIT`  
 防止建立共用檔案描述項。  
  
 `_O_RANDOM`  
 指定針對但不限於磁碟的隨機存取進行快取最佳化。  
  
 `_O_RDONLY`  
 開啟檔案為僅供讀取。 指定時無法搭配 `_O_RDWR` 或 `_O_WRONLY`。  
  
 `_O_RDWR`  
 開啟檔案以進行讀取和寫入。 指定時無法搭配 `_O_RDONLY` 或 `_O_WRONLY`。  
  
 `_O_SEQUENTIAL`  
 指定針對但不限於磁碟的循序存取進行快取最佳化。  
  
 `_O_TEXT`  
 以文字 (已轉譯) 模式開啟檔案 (如需詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](../../c-runtime-library/reference/fopen-wfopen.md))。  
  
 `_O_TRUNC`  
 開啟檔案，並將檔案截斷為零長度；檔案必須具有寫入權限。 指定時無法搭配 `_O_RDONLY`。 `_O_TRUNC` 用於搭配 `_O_CREAT` 以開啟現有檔案或建立檔案。  
  
> [!NOTE]
>  
          `_O_TRUNC` 旗標會終結指定檔案的內容。  
  
 `_O_WRONLY`  
 開啟檔案為僅供寫入。 指定時無法搭配 `_O_RDONLY` 或 `_O_RDWR`。  
  
 `_O_U16TEXT`  
 以 Unicode UTF-16 模式開啟檔案。  
  
 `_O_U8TEXT`  
 以 Unicode UTF-8 模式開啟檔案。  
  
 `_O_WTEXT`  
 以 Unicode 模式開啟檔案。  
  
 若要指定檔案存取模式，您必須指定 `_O_RDONLY`、`_O_RDWR` 或 `_O_WRONLY`。 存取模式沒有預設值。  
  
 若使用 `_O_WTEXT` 開啟檔案以供讀取，`_open` 會讀取檔案開頭，並檢查位元順序標記 (BOM)。 若有 BOM，會將檔案視為 UTF-8 或 UTF-16LE，這會取決於 BOM。 若無 BOM，會將檔案視為 ANSI。 使用 `_O_WTEXT` 開啟檔案以供寫入時，會使用 UTF-16。 無論之前的設定或位元順序標記為何，若使用 `_O_U8TEXT`，會一律將檔案開啟為 UTF-8；若使用 `_O_U16TEXT`，會一律將檔案開啟為 UTF-16。  
  
 使用 `_O_WTEXT`、`_O_U8TEXT` 或 `_O_U16TEXT` 以 Unicode 模式開啟檔案時，請輸入函式，將從檔案讀取的資料，轉譯為儲存為類型 `wchar_t` 的 UTF-16 資料。 寫入檔案的函示會以 Unicode 模式開啟，但包含儲存為類型 `wchar_t` 之 UTF-16 資料的緩衝區除外。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元組會導致參數驗證錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。  
  
 若搭配 `_open` (附加模式) 及 `_O_WRONLY|_O_APPEND`、`_O_WTEXT` 或 `_O_U16TEXT` 呼叫 `_O_U8TEXT`，會先嘗試開啟檔案以供讀取和寫入，再讀取 BOM，然後重新開啟檔案且僅供寫入。 若開啟檔案以供讀取和寫入失敗，則會僅針對寫入開啟檔案，並使用 Unicode 模式設定的預設值。  
  
 當使用兩個以上的資訊清單常數形成 `oflag` 引數時，會使用位元 OR 運算子 (`|`) 聯結常數。 如需二進位及文字模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
 指定 `pmode` 時，才需要 `_O_CREAT` 引數。 若檔案已存在，會忽略 `pmode`。 否則，`pmode` 會指定檔案權限設定 (新檔案第一次關閉時會進行此設定)。 `_open` 會在設定權限之前，將目前的檔案權限遮罩套用至 `pmode` (如需詳細資訊，請參閱 [_umask](../../c-runtime-library/reference/umask.md))。`pmode` 是整數運算式，包含一或兩個定義於 \<sys\stat.h> 中的下列資訊清單常數。  
  
 `_S_IREAD`  
 只允許讀取。  
  
 `_S_IWRITE`  
 允許寫入 (實際上允許讀取和寫入)。  
  
 `_S_IREAD`  `|`  `_S_IWRITE`  
 允許讀取和寫入。  
  
 指定兩個常數時，會使用位元 OR 運算子 (`|`) 加以聯結。 在 Windows 所有檔案皆為可讀取；不提供僅限寫入的權限。 因此，模式 `_S_IWRITE` 和 `_S_IREAD` `|` `_S_IWRITE` 相同。  
  
 若針對 `pmode` 指定了 `_S_IREAD` 和 `_S_IWRITE` 組合以外的值，那麼即使在其他作業系統是指定有效的 `pmode`，或是指定了允許的 `oflag` 值以外的任何值，函式也會以偵錯模式產生判斷提示，並叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回 -1 並將 `errno` 設定為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_open`|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|  
|`_wopen`|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|  
  
 `_open` 和 `_wopen` 是 Microsoft 擴充功能。 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="output"></a>輸出  
  
```  
Open succeeded on input file  
Open succeeded on output file  
```  
  
## <a name="see-also"></a>另請參閱  
 [低層級 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_sopen、_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)
