---
title: _sopen_s、_wsopen_s
ms.date: 11/04/2016
api_name:
- _sopen_s
- _wsopen_s
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
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: f21c805cae74fb700aa186a279082ee183db34d3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150832"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s、_wsopen_s

開啟檔案以供共用。 這些版本的 [_sopen 和 _wsopen](sopen-wsopen.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t _sopen_s(
   int* pfh,
   const char *filename,
   int oflag,
   int shflag,
   int pmode
);
errno_t _wsopen_s(
   int* pfh,
   const wchar_t *filename,
   int oflag,
   int shflag,
   int pmode,
);
```

### <a name="parameters"></a>參數

*pfh*<br/>
檔案控制代碼，如果有錯誤，則為 -1。

*filename*<br/>
檔案名稱。

*oflag*<br/>
允許的作業類型。

*shflag*<br/>
允許的共用類型。

*pmode*<br/>
權限設定。

## <a name="return-value"></a>傳回值

非零傳回值表示發生錯誤;在此情況下， **errno**會設定為下列其中一個值。

|errno 值|條件|
|-|-|
| **EACCES** |  指定的路徑是目錄，或者檔案為唯讀，但已嘗試「開啟以供寫入」作業。 |
| **EEXIST** |  已指定 **_O_CREAT**和 **_O_EXCL**旗標，但是*filename*已經存在。 |
| **EINVAL** |  不正確*oflag*、 *shflag*或*pmode*引數，或*pfh*或*filename*為 null 指標。 |
| **EMFILE** | 沒有更多可用的檔案描述元。 |
| **ENOENT** | 找不到檔案或路徑。 |

如果將無效引數傳遞至函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，並會傳回**EINVAL** 。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果發生錯誤，則會透過*pfh*傳回-1 （除非*pfh*是 null 指標）。

## <a name="remarks"></a>備註

**_Sopen_s**函式會開啟*filename*所指定的檔案，並準備檔案以供共用讀取或寫入（如*oflag*和*shflag*所定義）。 **_wsopen_s**是寬字元版本的 **_sopen_s**; **_wsopen_s**的*filename*引數是寬字元字串。 相反地， **_wsopen_s**和 **_sopen_s**的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

整數運算式*oflag*是藉由結合一或多個在 \<fcntl.h> > 中定義的資訊清單常數所組成。 當兩個或多個常數形成引數*oflag*時，它們會與位 or 運算子（ **&#124;** ）結合。

|*oflag*常數|行為|
|-|-|
| **_O_APPEND** | 在每次寫入作業之前，將檔案指標移到檔案的結尾。 |
| **_O_BINARY** | 以二進位 (未轉譯) 模式開啟檔案 (如需二進位模式的說明，請參閱 [fopen](fopen-wfopen.md))。 |
| **_O_CREAT** | 建立檔案並開啟以供寫入。 若*filename*指定的檔案存在，則不會有任何作用。 當指定 **_O_CREAT**時， *pmode*引數是必要的。 |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | 將檔案建立為暫存檔，若有可能的話，請勿清除至磁碟。 當指定 **_O_CREAT**時， *pmode*引數是必要的。 |
| **_O_CREAT** &#124; **_O_TEMPORARY** | 將檔案建立為暫存檔；當最後一個檔案描述項關閉時會刪除檔案。 當指定 **_O_CREAT**時， *pmode*引數是必要的。 |
| **_O_CREAT** &#124; `_O_EXCL` | 如果*filename*指定的檔案存在，則會傳回錯誤值。 僅適用于與 **_O_CREAT**搭配使用時。 |
| **_O_NOINHERIT** | 防止建立共用檔案描述項。 |
| **_O_RANDOM** | 指定針對但不限於磁碟的隨機存取進行快取最佳化。 |
| **_O_RDONLY** | 開啟檔案為僅供讀取。 不能以 **_O_RDWR**或 **_O_WRONLY**指定。 |
| **_O_RDWR** | 開啟檔案以進行讀取和寫入。 不能以 **_O_RDONLY**或 **_O_WRONLY**指定。 |
| **_O_SEQUENTIAL** | 指定針對但不限於磁碟的循序存取進行快取最佳化。 |
| **_O_TEXT** | 以文字 (已轉譯) 模式開啟檔案 (如需詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](fopen-wfopen.md))。 |
| **_O_TRUNC** | 開啟檔案，並將檔案截斷為零長度；檔案必須具有寫入權限。 不能與 **_O_RDONLY**一起指定。 搭配 **_O_CREAT**使用的 **_O_TRUNC**會開啟現有檔案或建立檔案。 **注意：** **_O_TRUNC**旗標會終結指定檔案的內容。 |
| **_O_WRONLY** | 將檔案開啟為僅供寫入。 不能以 **_O_RDONLY**或 **_O_RDWR**指定。 |
| **_O_U16TEXT** | 以 Unicode UTF-16 模式開啟檔案。 |
| **_O_U8TEXT** | 以 Unicode UTF-8 模式開啟檔案。 |
| **_O_WTEXT** | 以 Unicode 模式開啟檔案。 |

若要指定檔案存取模式，您必須指定 [ **_O_RDONLY**]、[ **_O_RDWR**] 或 [ **_O_WRONLY**]。 存取模式沒有預設值。

當使用 **_O_WTEXT**、 **_O_U8TEXT**或 **_O_U16TEXT**以 Unicode 模式開啟檔案時，輸入函式會將從檔案讀取的資料轉譯為儲存為類型**wchar_t**的 utf-16 資料。 寫入以 Unicode 模式開啟之檔案的函式，會預期包含以類型**wchar_t**儲存之 utf-16 資料的緩衝區。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元組會導致參數驗證錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。

如果以 **_O_WRONLY** |  **_O_APPEND** （附加模式）和 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**呼叫 **_sopen_s** ，它會先嘗試開啟檔案進行讀取和寫入、讀取 BOM，然後重新開啟它以供寫入。 若開啟檔案以供讀取和寫入失敗，則會僅針對寫入開啟檔案，並使用 Unicode 模式設定的預設值。

引數*shflag*是常數運算式，由下列其中一個資訊清單常數所組成，它們是在 \<share. h > 中定義。

|*shflag*常數|行為|
|-|-|
| **_SH_DENYRW** | 拒絕對檔案的讀取和寫入存取。 |
| **_SH_DENYWR** | 拒絕對檔案的寫入存取。 |
| **_SH_DENYRD** | 拒絕對檔案的讀取存取。 |
| **_SH_DENYNO** | 允許讀取及寫入權限。 |

*Pmode*引數一律是必要的，不同于 **_sopen**。 當您指定 **_O_CREAT**時，如果檔案不存在， *pmode*就會指定檔案的許可權設定，這會在第一次關閉新檔案時設定。 否則，會忽略*pmode* 。 *pmode*是一個整數運算式，其中包含 **_S_IWRITE**和 **_S_IREAD**的其中一個或兩個資訊清單常數，它們是在 \<sys\stat.h > 中定義。 指定兩個常數時，會使用位元 OR 運算子加以結合。 *Pmode*的意義如下所示。

|*pmode*|意義|
|-|-|
| **_S_IREAD** | 只允許讀取。 |
| **_S_IWRITE** | 允許寫入 (實際上允許讀取和寫入)。 |
| **_S_IREAD** &#124; **_S_IWRITE** | 允許讀取和寫入。 |

若沒有指定寫入權限，則檔案為唯讀。 在 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此， **_S_IWRITE**和 **_S_IREAD** |  **_S_IWRITE**的模式是相等的。

**_sopen_s**在設定許可權之前，將目前的檔案許可權遮罩套用至*pmode* 。 (請參閱 [_umask](umask.md))。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|
|**_wsopen_s**|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys/types.h>、\<sys/stat.h>、\<share.h>|

**_sopen_s**和 **_wsopen_s**是 Microsoft 擴充功能。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_locking](locking.md) 的範例。

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_fsopen、_wfsopen](fsopen-wfsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
