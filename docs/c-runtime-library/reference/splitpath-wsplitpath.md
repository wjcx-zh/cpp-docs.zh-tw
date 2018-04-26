---
title: _splitpath、_wsplitpath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wsplitpath
- _splitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
dev_langs:
- C++
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29102810363e6501d622ac065b63d0bfe978911a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="splitpath-wsplitpath"></a>_splitpath、_wsplitpath

將一個路徑名稱分割為多個元件。 這些函式已有更安全的版本可供使用，請參閱 [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)。

## <a name="syntax"></a>語法

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>參數

*路徑*完整路徑。

*磁碟機*磁碟機代號，後面接著冒號 (**:**)。 您可以傳遞**NULL**這個參數，如果您不需要的磁碟機代號。

*dir*目錄路徑，包括結尾的斜線。 正斜線 ( **/** )、 反斜線 ( **\\** )，或兩者都可能使用。 您可以傳遞**NULL**這個參數，如果您不需要的目錄路徑。

*fname*基底檔案名稱 （沒有副檔名）。 您可以傳遞**NULL**這個參數，如果您不需要檔案名稱。

*ext*檔案的副檔名，包括前置週期 (**。**)。 您可以傳遞**NULL**這個參數，如果您不需要檔名的副檔名。

## <a name="remarks"></a>備註

**_Splitpath**函式分成四個元件的路徑。 **_splitpath**自動多位元組字元字串引數處理為適當且可辨識的多位元組字元序列，會根據目前使用中的多位元組字碼頁。 **_wsplitpath**是寬字元版本的 **_splitpath**; 的引數 **_wsplitpath**是寬字元字串。 除此之外，這些函式的行為相同。

**安全性提示**這些函式可能會帶來緩衝區滿溢問題所引發的威脅。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 這些函式已有更安全的版本可供使用，請參閱 [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

每個元件的完整路徑儲存在個別的緩衝區。資訊清單常數 **_MAX_DRIVE**， **_MAX_DIR**， **_MAX_FNAME**，和 **_MAX_EXT** （定義於 STDLIB。H） 指定每個檔案元件的最大大小。 大於對應資訊清單常數的檔案元件會造成堆積損毀。

每個緩衝區都必須與其對應的資訊清單常數一樣大，以避免潛在緩衝區滿溢。

下表列出資訊清單常數的值。

|名稱|值|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

如果完整路徑未包含的元件 （例如，檔案名稱）， **_splitpath**指派空白對應緩衝區的字串。

您可以傳遞**NULL**至 **_splitpath**以外的任何參數*路徑*，您不需要。

如果*路徑*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**EINVAL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_makepath](makepath-wmakepath.md) 的範例。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
