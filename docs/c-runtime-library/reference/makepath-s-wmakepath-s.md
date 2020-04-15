---
title: _makepath_s、_wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 3a44651cb9ff8be806c45c6b6c5f41f810319a85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341595"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s、_wmakepath_s

從元件建立路徑名稱。 這些是 [_makepath、_wmakepath](makepath-wmakepath.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>參數

*路徑*<br/>
完整路徑緩衝區。

*大小字內*<br/>
以字組為單位的緩衝區大小。

*大小位元組*<br/>
以位元組為單位的緩衝區大小。

*驅動*<br/>
包含對應至所需磁碟機的代號 (A、B 等) 及選擇性後置冒號。 如果缺少冒號 **,_makepath_s**會自動在複合路徑中插入冒號。 如果*驅動器*為**NULL**或指向空字串,則複合*路徑*字串中不會顯示驅動器號。

*dir*<br/>
包含目錄路徑，但不包含磁碟機指示項或實際檔案名稱。 尾隨斜杠是可選的,在單個*dir*參數中可以使用前\\斜杠 (/) 或反斜杠 () 或兩者。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果*dir*為**NULL**或指向空字串,則複合路徑字串中未插入任何目錄*路徑*。

*fname*<br/>
包含基底檔案名稱，但不包含任何副檔名。 如果*fname*為**NULL**或指向空字串,則複合*路徑*字串中未插入任何檔案名。

*內線*<br/>
包含實際副檔名，可包含或不含前置句號 (.)。 如果期間未顯示在*分機*中 **,_makepath_s**自動插入該期間。如果*分機*為**NULL**或指向空字串,則複合*路徑*字串中不會插入任何擴展。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*路徑*|*大小以* / *位元組為單位*|傳回|*路徑*內容|
|------------|------------------------------------|------------|------------------------|
|**空**|任意|**埃因瓦爾**|未修改|
|任意|<= 0|**埃因瓦爾**|未修改|

如果發生上述任何一種錯誤狀況，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續 **,errno**設定為**EINVAL,** 函數傳回**EINVAL**。 **允許參數***驅動器**、fname*和*ext*的 NULL。有關這些參數為空指標或空字串時的行為的資訊,請參閱備註部分。

## <a name="remarks"></a>備註

**_makepath_s**函數從單個元件創建複合路徑字串,將結果存儲在*路徑*中。 *路徑*可能包括驅動器號、目錄路徑、檔名和檔名副檔名。 **_wmakepath_s**是 **_makepath_s**的寬字元版本;要 **_wmakepath_s**的參數是寬字元字串。 **_wmakepath_s****和_makepath_s**行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*路徑*參數必須指向足夠大以容納完整路徑的空緩衝區。 複合*路徑*不能大於在 Stdlib.h 中定義的 **_MAX_PATH**常量。

如果路徑為**NULL,** 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 此外 **,errno**設定為**EINVAL**。 所有其他參數都允許**NULL**值。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
