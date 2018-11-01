---
title: _makepath_s、_wmakepath_s
ms.date: 11/04/2016
apiname:
- _wmakepath_s
- _makepath_s
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
apitype: DLLExport
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
ms.openlocfilehash: 6914299dd7ede97c9004dcc95e01b1a35188f5c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471912"
---
# <a name="makepaths-wmakepaths"></a>_makepath_s、_wmakepath_s

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

*path*<br/>
完整路徑緩衝區。

*sizeInWords*<br/>
以字組為單位的緩衝區大小。

*sizeInBytes*<br/>
以位元組為單位的緩衝區大小。

*磁碟機*<br/>
包含對應至所需磁碟機的代號 (A、B 等) 及選擇性後置冒號。 **_makepath_s**冒號自動插入複合路徑中遺失。 如果*磁碟機*是**NULL**或指向空字串，不要的磁碟機代號會出現在複合*路徑*字串。

*dir*<br/>
包含目錄路徑，但不包含磁碟機指示項或實際檔案名稱。 結尾的斜線是選擇性的並正斜線 （/） 或反斜線 (\\)，或是兩者都可能會用於在單一*dir*引數。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果*dir*是**NULL**或指向空字串，沒有目錄路徑會插入複合*路徑*字串。

*fname*<br/>
包含基底檔案名稱，但不包含任何副檔名。 如果*fname*是**NULL**或指向空字串，任何檔名會插入複合*路徑*字串。

*ext*<br/>
包含實際副檔名，可包含或不含前置句號 (.)。 **_makepath_s**自動插入句號，如果它不會出現在*ext*。如果*ext*是**NULL**或指向空字串，不含副檔名會插入複合*路徑*字串。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*path*|*sizeInWords* / *sizeInBytes*|Return|內容*路徑*|
|------------|------------------------------------|------------|------------------------|
|**NULL**|any|**EINVAL**|未修改|
|any|<= 0|**EINVAL**|未修改|

如果發生上述任何一種錯誤狀況，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回**EINVAL**。 **NULL**允許的參數*磁碟機*， *fname*，和*ext*。如需這些參數為 null 指標或空字串時之行為的資訊，請參閱＜備註＞一節。

## <a name="remarks"></a>備註

**_Makepath_s**函式會從 個別元件，儲存在結果中建立複合路徑字串*路徑*。 *路徑*可能包含磁碟機代號、 目錄路徑、 檔名和副檔名。 **_wmakepath_s**是寬字元版本的 **_makepath_s**; 的引數 **_wmakepath_s**是寬字元字串。 **_wmakepath_s**並 **_makepath_s**行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*路徑*引數必須指向空的緩衝區不夠大，無法容納完整路徑。 複合*路徑*必須是不能大於 **_MAX_PATH**在 Stdlib.h 中定義的常數。

如果路徑**NULL**，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 颾魤 ㄛ **errno**設為**EINVAL**。 **NULL**允許所有其他參數的值。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
