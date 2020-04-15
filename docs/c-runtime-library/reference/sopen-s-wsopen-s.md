---
title: _sopen_s、_wsopen_s
ms.date: 4/2/2020
api_name:
- _sopen_s
- _wsopen_s
- _o__sopen_s
- _o__wsopen_s
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
ms.openlocfilehash: 81feacae0e4608512e7325c57e7f2b96bcf2cdde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356508"
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

*普夫*<br/>
檔案控制代碼，如果有錯誤，則為 -1。

*檔案名稱*<br/>
檔案名稱

*拉格*<br/>
允許的作業種類。

*什弗拉格*<br/>
容許的共用種類。

*pmode*<br/>
權限設定。

## <a name="return-value"></a>傳回值

非零返回值表示錯誤;因此,返回值為錯誤。在這種情況下 **,errno**設置為以下值之一。

|errno 值|條件|
|-|-|
| **EACCES** |  指定的路徑為目錄，或是檔案為唯讀，但已嘗試「開啟以供寫入」作業。 |
| **EEXIST** |  **_O_CREAT**和 **_O_EXCL**標誌已指定,但*檔名*已存在。 |
| **埃因瓦爾** |  無效*的無拉格**、shflag*或*pmode*參數,或*pfh*或*檔名*是一個空指標。 |
| **EMFILE** | 沒有更多可用的檔案描述元。 |
| **埃諾恩特** | 找不到檔案或路徑。 |

如果將無效引數傳遞至函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,**則將 errno**設定為**EINVAL,** 並傳回**EINVAL。**

有關這些代碼和其他返回代碼的詳細資訊,請參閱[errno、_doserrno、_sys_errlist和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果出現錯誤,則通過*pfh*返回 -1(除非*pfh*是空指標)。

## <a name="remarks"></a>備註

**_sopen_s**函數打開*檔案名*指定的檔案,並準備檔進行共用讀取或寫入,由*lag*和*shflag*定義。 **_wsopen_s**是 **_sopen_s**的寬字元版本;要 **_wsopen_s***的檔案名*參數是寬字元字串。 **_wsopen_s****和_sopen_s**行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

*lag 的*整數運算式是通過組合一個或多個清單常量而形成的,這些常量在 fcntl.h>中\<定義。 當兩個或多個常量形成 lag*參數*時,它們與位-OR 運算符 **(&#124;** ) 結合使用。

|*滯後*常數|行為|
|-|-|
| **_O_APPEND** | 在每次寫入作業之前，將檔案指標移到檔案的結尾。 |
| **_O_BINARY** | 以二進位 (未轉譯) 模式開啟檔案 (如需二進位模式的說明，請參閱 [fopen](fopen-wfopen.md))。 |
| **_O_CREAT** | 建立檔案並開啟以供寫入。 如果存在*檔案名*指定的檔案,則無效。 指定 **_O_CREAT**時,需要*pmode*參數。 |
| **_O_CREAT&#124;_O_SHORT_LIVED** **_O_SHORT_LIVED** | 將檔案建立為暫存檔，若有可能的話，請勿清除至磁碟。 指定 **_O_CREAT**時,需要*pmode*參數。 |
| **_O_CREAT&#124;_O_TEMPORARY** **_O_TEMPORARY** | 將檔案建立為暫存檔；當最後一個檔案描述項關閉時會刪除檔案。 指定 **_O_CREAT**時,需要*pmode*參數。 |
| **_O_CREAT&#124;**`_O_EXCL` | 如果存在*由檔名*指定的檔,則返回錯誤值。 僅適用於**與_O_CREAT**一起使用時。 |
| **_O_NOINHERIT** | 防止建立共用檔案描述項。 |
| **_O_RANDOM** | 指定針對但不限於磁碟的隨機存取進行快取最佳化。 |
| **_O_RDONLY** | 開啟檔案為僅供讀取。 不能用 **_O_RDWR**或 **_O_WRONLY**指定。 |
| **_O_RDWR** | 開啟檔案以進行讀取和寫入。 不能用 **_O_RDONLY**或 **_O_WRONLY**指定。 |
| **_O_SEQUENTIAL** | 指定針對但不限於磁碟的循序存取進行快取最佳化。 |
| **_O_TEXT** | 以文字 (已轉譯) 模式開啟檔案 (如需詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](fopen-wfopen.md))。 |
| **_O_TRUNC** | 開啟檔案，並將檔案截斷為零長度；檔案必須具有寫入權限。 無法使用 **_O_RDONLY**指定 。 **_O_TRUNC**與 **_O_CREAT**一起打開現有檔或創建檔。 **註:****_O_TRUNC**標誌銷毀指定文件的內容。 |
| **_O_WRONLY** | 將檔案開啟為僅供寫入。 不能用 **_O_RDONLY**或 **_O_RDWR**指定。 |
| **_O_U16TEXT** | 以 Unicode UTF-16 模式開啟檔案。 |
| **_O_U8TEXT** | 以 Unicode UTF-8 模式開啟檔案。 |
| **_O_WTEXT** | 以 Unicode 模式開啟檔案。 |

要指定檔案存取模式,必須指定 **_O_RDONLY、_O_RDWR**或 **_O_RDWR****_O_WRONLY**。 存取模式沒有預設值。

當使用 **_O_WTEXT、_O_U8TEXT**或 **_O_U16TEXT**在 **_O_U8TEXT**Unicode 模式下 開啟檔時,輸入函數會將從檔案中讀取的數據轉換為作為類型**wchar_t**儲存的 UTF-16 資料。 寫入在 Unicode 模式開啟的檔案的函數需要包含 UTF-16 資料的緩衝區儲存為**型態wchar_t**。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元組會導致參數驗證錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。

如果使用 | **_O_WRONLY_O_APPEND(** 追加模式 **_O_WRONLY**)和 **_O_WTEXT、_O_U16TEXT****_O_U16TEXT**或 **_O_U8TEXT**調用 **_sopen_s,** 它首先嘗試打開檔案進行讀取和寫入,讀取 BOM,然後重新打開它僅用於寫入。 若開啟檔案以供讀取和寫入失敗，則會僅針對寫入開啟檔案，並使用 Unicode 模式設定的預設值。

參數*shflag*是一個常量運算式,由以下清單常量之一組成,\<這些常 量在 share.h>中定义。

|*什弗拉格*常數|行為|
|-|-|
| **_SH_DENYRW** | 拒絕對檔案的讀取和寫入存取。 |
| **_SH_DENYWR** | 拒絕對檔案的寫入存取。 |
| **_SH_DENYRD** | 拒絕對檔案的讀取存取。 |
| **_SH_DENYNO** | 允許讀取和寫入存取。 |

*pmode*參數始終是必要的,_sopen**中不同**。 指定 **_O_CREAT**時,如果檔不存在 *,pmode*會指定檔的許可權設置,這些設置在第一次關閉新檔時設置。 否則,*將忽略 pmode。* *pmode*是一個整數運算式,它包含一個或兩個清單常量 **_S_IWRITE**和 **_S_IREAD**,這些常量\<在 sys_stat.h>中定义。 指定兩個常數時，會使用位元 OR 運算子加以結合。 *pmode*的含義如下。

|*pmode*|意義|
|-|-|
| **_S_IREAD** | 只允許讀取。 |
| **_S_IWRITE** | 允許寫入。 (實際上允許讀取和寫入)。 |
| **_S_IREAD&#124;_S_IWRITE** **_S_IWRITE** | 允許讀取和寫入。 |

若沒有指定寫入權限，則檔案為唯讀。 在 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此 **,_S_IWRITE_S_IWRITE****和_S_IREAD** | **模式是等效**的。

**_sopen_s**在設置許可權之前將當前文件許可權掩碼應用於*pmode。* (請參閱 [_umask](umask.md))。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|
|**_wsopen_s**|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys/types.h>、\<sys/stat.h>、\<share.h>|

**_sopen_s**和 **_wsopen_s**是微軟的擴展。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_locking](locking.md) 的範例。

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_fsopen、_wfsopen](fsopen-wfsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
