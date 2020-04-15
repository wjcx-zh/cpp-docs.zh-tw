---
title: _splitpath_s、_wsplitpath_s
ms.date: 4/2/2020
api_name:
- _wsplitpath_s
- _splitpath_s
- _o__splitpath_s
- _o__wsplitpath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: 364544a9423668494747405e801d59b73de4e6c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355624"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s、_wsplitpath_s

將一個路徑名稱分割為多個元件。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_splitpath、_wsplitpath](splitpath-wsplitpath.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>參數

*路徑*<br/>
完整路徑。

*驅動*<br/>
驅動器號,後跟冒號 (**。** 如果不需要驅動器號,可以傳遞此參數的**NULL。**

*磁碟數量元素*<br/>
*驅動器*緩衝區的大小(以單位元組或寬字元表示)。 如果*驅動器*為**NULL,** 則此值必須為 0。

*dir*<br/>
目錄路徑，包括結尾斜線。 可使用向前斜**/** 杠 ()、斜**\\**杠 () 或兩者。 如果不需要目錄路徑,可以傳遞此參數的**NULL。**

*元素的底數*<br/>
以單位元組或寬字元表示*的 dir*緩衝區的大小。 如果*dir*為**NULL,** 則此值必須為 0。

*fname*<br/>
基底檔名 (不含副檔名)。 如果不需要檔名,可以傳遞此參數的**NULL。**

*名稱 元素數量*<br/>
以單位元組或寬字元表示*fname*緩衝區的大小。 如果*fname*為**NULL,** 則此值必須為 0。

*內線*<br/>
檔案名副檔名,包括前導期 **(. 。** 如果不需要檔案名副檔名,可以傳遞此參數的**NULL。**

*元素的分量*<br/>
以單位元組或寬字元表示*的 ext*緩衝區的大小。 如果*分機*為**NULL,** 則此值必須為 0。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|條件|傳回值|
|---------------|------------------|
|*路徑*為**NULL**|**埃因瓦爾**|
|*驅動器*為**NULL,***磁碟機數元素*為非零|**埃因瓦爾**|
|*驅動器*是非**NULL,***磁碟機數元素*數為零|**埃因瓦爾**|
|*dir*為**NULL,***迪線元素為*非零|**埃因瓦爾**|
|*dir*是非**NULL,***迪值元素數*為零|**埃因瓦爾**|
|*fname*為**NULL,***名稱為元素編號*為非零|**埃因瓦爾**|
|*fname*是非**NULL,***名稱元素數*為零|**埃因瓦爾**|
|*ext*為**NULL,***元素的分量*為非零|**埃因瓦爾**|
|*ext*是非**NULL,***元素的分值為*零|**埃因瓦爾**|

如果發生上述任何狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將**errno**設定為**EINVAL**並傳回**EINVAL**。

如果任何緩衝區太短而無法儲存結果,這些函數將清除所有緩衝區為空字串,將**errno**設定為**ERANGE,** 並傳回**ERANGE**。

## <a name="remarks"></a>備註

**_splitpath_s**函數將路徑分解為四個元件。 **_splitpath_s**根據需要自動處理多位元位元串參數,根據當前使用的多位元組碼頁識別多位元組位元序列。 **_wsplitpath_s**是 **_splitpath_s**的寬字元版本;要 **_wsplitpath_s**的參數是寬字元字串。 否則，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

完整路徑的每個元件都存儲在單獨的緩衝區中;清單常量 **_MAX_DRIVE、_MAX_DIR、_MAX_FNAME**和 **_MAX_EXT(** 在 STDLIB 中定義)。 **_MAX_DRIVE** **_MAX_FNAME**H) 為每個檔案元件指定最大允許大小。 大於對應資訊清單常數的檔案元件會造成堆積損毀。

下表列出資訊清單常數的值。

|名稱|值|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

如果完整路徑不包含元件(例如檔名 **),_splitpath_s**將空字串分配給相應的緩衝區。

在 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md) 的範例。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
