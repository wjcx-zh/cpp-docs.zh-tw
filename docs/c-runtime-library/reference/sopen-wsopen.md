---
title: _sopen、_wsopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _sopen
- _wsopen
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
- _wsopen
- wsopen
- _sopen
- _tsopen
dev_langs:
- C++
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8d7f7624dc8c521186aa697ad8825c77e0108f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sopen-wsopen"></a>_sopen、_wsopen

開啟檔案以供共用。 這些函式更安全的版本可用： 請參閱[_sopen_s、 _wsopen_s](sopen-s-wsopen-s.md)。

## <a name="syntax"></a>語法

```C
int _sopen(
   const char *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
int _wsopen(
   const wchar_t *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
```

### <a name="parameters"></a>參數

*filename*<br/>
檔案名稱

*oflag*<br/>
允許的作業類型。

*shflag*<br/>
允許的共用類型。

*pmode*<br/>
權限設定。

## <a name="return-value"></a>傳回值

這些函式每一個都會傳回已開啟檔案的檔案描述項。

如果*filename*或*oflag*是**NULL**指標，或如果*oflag*或*shflag*不在有效範圍值的無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回-1，並設定**errno**至下列值之一。

|errno 值|條件|
|-|-|
**EACCES**|指定的路徑為目錄，或是檔案為唯讀，但已嘗試「開啟以供寫入」作業。
**EEXIST**|**_O_CREAT**和 **_O_EXCL**指定旗標，但*filename*已經存在。
**EINVAL**|無效*oflag*或*shflag*引數。
**EMFILE**|沒有更多檔案描述項可用。
**ENOENT**|找不到檔案或路徑。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Sopen**函式會開啟所指定的檔案*filename*並準備檔案以供共用的讀取或寫入，所定義的*oflag*和*shflag*. **_wsopen**是寬字元版本的 **_sopen**; *filename*引數 **_wsopen**是寬字元字串。 **_wsopen**和 **_sopen**除此之外的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

整數運算式*oflag*的一或多個下列中定義的資訊清單常數形成\<.h >。 當兩個或多個常數形成引數*oflag*，可結合的位元 OR 運算子 ( **&#124;** )。

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

以 Unicode 模式開啟檔案是時，使用 **_O_WTEXT**， **_O_U8TEXT**，或 **_O_U16TEXT**，請輸入函式轉譯成 utf-16 資料從檔案讀取資料儲存為類型**wchar_t**。 寫入至以 Unicode 模式開啟檔案的函式預期會包含儲存為類型的 utf-16 資料的緩衝區**wchar_t**。 若檔案是編碼為 UTF-8，則會在寫入 UTF-16 資料時轉譯為 UTF-8，且會在讀取檔案的 UTF-8 編碼內容時轉譯成 UTF-16。 嘗試以 Unicode 模式讀取或寫入奇數位元組會導致參數驗證錯誤。 若要讀取或寫入作為 UTF-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。 您要負責所有必要的編碼轉譯。

如果 **_sopen**呼叫 **_O_WRONLY** | **_O_APPEND** （附加模式） 和 **_O_WTEXT**， **_O_U16TEXT**，或 **_O_U8TEXT**，它會先嘗試開啟檔案進行讀取和寫入，讀取 BOM，然後重新開啟它僅供寫入。 若開啟檔案以供讀取和寫入失敗，則會僅針對寫入開啟檔案，並使用 Unicode 模式設定的預設值。

引數*shflag*是常數運算式，其中包含下列中定義的資訊清單常數之一\<share.h >。

|*shflag*常數|行為|
|-|-|
**_SH_DENYRW**|拒絕對檔案的讀取和寫入存取。
**_SH_DENYWR**|拒絕對檔案的寫入存取。
**_SH_DENYRD**|拒絕對檔案的讀取存取。
**_SH_DENYNO**|允許讀取及寫入權限。

*Pmode*引數是需要時才 **_O_CREAT**指定。 如果檔案不存在， *pmode*指定新檔案第一次關閉時會進行此設定檔的權限設定。 否則， *pmode*會被忽略。 *pmode*是整數運算式，其中包含一或兩個資訊清單常數 **_S_IWRITE**和 **_S_IREAD**，定義所在\<sys\stat.h >。 指定兩個常數時，會使用位元 OR 運算子加以結合。 意義*pmode*如下所示。

|*pmode*|意義|
|-|-|
**_S_IREAD**|只允許讀取。
**_S_IWRITE**|允許寫入 (實際上允許讀取和寫入)。
**_S_IREAD** &AMP;#124; **_S_IWRITE**|允許讀取和寫入。

若沒有指定寫入權限，則檔案為唯讀。 在 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。 因此，模式 **_S_IWRITE**和 **_S_IREAD** | **_S_IWRITE**相等。

**_sopen**目前檔案權限遮罩套用至*pmode*之前已設定權限。 (請參閱 [_umask](umask.md))。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|
|**_wsopen**|\<io.h> 或 \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_locking](locking.md) 的範例。

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_fsopen、_wfsopen](fsopen-wfsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
