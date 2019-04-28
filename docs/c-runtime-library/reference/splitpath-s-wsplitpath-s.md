---
title: _splitpath_s、_wsplitpath_s
ms.date: 11/04/2016
apiname:
- _wsplitpath_s
- _splitpath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 87af8bac525844c06fdfc16d7d13a06eef4d61ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62355025"
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s、_wsplitpath_s

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

*path*<br/>
完整路徑。

*drive*<br/>
磁碟機代號，後面接著冒號 (**:**)。 您可以傳遞**NULL**此參數，如果您不需要的磁碟機代號。

*driveNumberOfElements*<br/>
大小*磁碟機*以單一位元組或寬字元為單位的緩衝區。 如果*磁碟機*是**NULL**，這個值必須是 0。

*dir*<br/>
目錄路徑，包括結尾斜線。 正斜線 ( **/** )，反斜線 ( **\\** )，或可以使用。 您可以傳遞**NULL**此參數，如果您不需要的目錄路徑。

*dirNumberOfElements*<br/>
大小*dir*以單一位元組或寬字元為單位的緩衝區。 如果*dir*是**NULL**，這個值必須是 0。

*fname*<br/>
基底檔名 (不含副檔名)。 您可以傳遞**NULL**此參數，如果您不需要檔案名稱。

*nameNumberOfElements*<br/>
大小*fname*以單一位元組或寬字元為單位的緩衝區。 如果*fname*是**NULL**，這個值必須是 0。

*ext*<br/>
副檔名，包括前置句點 (**。**)。您可以傳遞**NULL**此參數，如果您不需要檔名的副檔名。

*extNumberOfElements*<br/>
大小*ext*以單一位元組或寬字元為單位的緩衝區。 如果*ext*是**NULL**，這個值必須是 0。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|條件|傳回值|
|---------------|------------------|
|*路徑*是**NULL**|**EINVAL**|
|*磁碟機*已**NULL**， *driveNumberOfElements*為非零|**EINVAL**|
|*磁碟機*是非**NULL**， *driveNumberOfElements*為零|**EINVAL**|
|*dir*已**NULL**， *dirNumberOfElements*為非零|**EINVAL**|
|*dir*是非**NULL**， *dirNumberOfElements*為零|**EINVAL**|
|*fname*已**NULL**， *nameNumberOfElements*為非零|**EINVAL**|
|*fname*是非**NULL**， *nameNumberOfElements*為零|**EINVAL**|
|*ext*已**NULL**， *extNumberOfElements*為非零|**EINVAL**|
|*ext*是非**NULL**， *extNumberOfElements*為零|**EINVAL**|

如果發生上述任何狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**要**EINVAL** ，並傳回**EINVAL**。

如果任何緩衝區太短而無法保留結果，這些函式將所有緩衝區都清除成空字串、 設定**errno**要**ERANGE**，並傳回**ERANGE**。

## <a name="remarks"></a>備註

**_Splitpath_s**函式會分成四個元件中的路徑。 **_splitpath_s**自動多位元組字元字串引數處理為適當，辨識多位元組字元序列，根據目前使用中的多位元組字碼頁。 **_wsplitpath_s**是寬字元版本的 **_splitpath_s**; 的引數 **_wsplitpath_s**是寬字元字串。 否則，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

完整路徑的每個元件都會儲存在個別的緩衝區;資訊清單常數 **_MAX_DRIVE**， **_MAX_DIR**， **_MAX_FNAME**，以及 **_MAX_EXT** （定義於 STDLIB。H） 指定每個檔案元件的最大容許大小。 大於對應資訊清單常數的檔案元件會造成堆積損毀。

下表列出資訊清單常數的值。

|名稱|值|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

如果完整路徑未包含的元件 （例如，檔名）， **_splitpath_s**將空字串指派給對應的緩衝區。

在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

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
