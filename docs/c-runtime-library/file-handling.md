---
title: 檔案處理 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.files
dev_langs:
- C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95971cceab5673755b33bd99c3365bee62610bf5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="file-handling"></a>檔案處理

使用這些常式以建立、刪除和管理檔案，並設定和檢查檔案存取權限。

C 執行階段程式庫同時開啟檔案數目的上限為 512。 嘗試開啟大於數目上限的檔案描述項或檔案資料流將導致程式發生錯誤。 請使用 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 變更此數字。

## <a name="file-handling-routines-file-descriptor"></a>檔案處理常式 (檔案描述項)

這些常式會對檔案描述項所指定的檔案進行操作。

|常式傳回的值|請使用|
|-------------|---------|
|[_chsize](../c-runtime-library/reference/chsize.md)、[_chsize_s](../c-runtime-library/reference/chsize-s.md)|變更檔案大小|
|[_filelength、_filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|取得檔案長度|
|[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|取得描述項的檔案狀態資訊|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|傳回與現有 C 執行階段檔案描述項相關聯的作業系統檔案控制代碼|
|[_isatty](../c-runtime-library/reference/isatty.md)|檢查字元裝置|
|[_locking](../c-runtime-library/reference/locking.md)|檔案鎖定區域|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|將 C 執行階段檔案描述項與現有作業系統檔案控制代碼產生關聯|
|[_setmode](../c-runtime-library/reference/setmode.md)|設定檔案轉譯模式|

## <a name="file-handling-routines-path-or-filename"></a>檔案處理常式 (路徑或檔案名稱)

這些常式會對由路徑或檔名指定的檔案進行操作。

|常式傳回的值|使用|
|-------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md)、 [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|檢查檔案權限設定|
|[_chmod、_wchmod](../c-runtime-library/reference/chmod-wchmod.md)|變更檔案權限設定|
|[_fullpath、_wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|將相對路徑展開為絕對路徑名稱|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md)、 [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|將路徑元件合併成單一的完整路徑|
|[_mktemp、 _wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)、 [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|建立唯一的檔名|
|[remove0、_wremove](../c-runtime-library/reference/remove-wremove.md)|刪除檔案|
|[rename、_wrename](../c-runtime-library/reference/rename-wrename.md)|重新命名檔案|
|[_splitpath、 _wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)、 [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|將路徑剖析成元件|
|[_stat、_stat64、_stati64、_wstat、_wstat64、_wstati64](../c-runtime-library/reference/stat-functions.md)|取得有關具名檔案的檔案狀態資訊|
|[_umask](../c-runtime-library/reference/umask.md)、 [_umask_s](../c-runtime-library/reference/umask-s.md)|將程式建立的新檔案設定為預設權限遮罩|
|[_unlink、_wunlink](../c-runtime-library/reference/unlink-wunlink.md)|刪除檔案|

## <a name="file-handling-routines-open-file"></a>檔案處理常式 (開啟檔案)

這些常式會開啟檔案。

|常式傳回的值|使用|
|-------------|---------|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)、 [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|開啟檔案並傳回此開啟檔案的指標。|
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|以檔案共用開啟資料流，並傳回此開啟檔案的指標。|
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|開啟檔案，並傳回檔案描述項至已開啟的檔案。|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)、 [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|以檔案共用開啟檔案，並傳回檔案描述項至該開啟檔案。|
|[_pipe](../c-runtime-library/reference/pipe.md)|建立用於讀取和寫入的管道。|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)、 [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|重新指派檔案指標。|

這些常式提供在 `FILE` 結構、檔案描述項和 Win32 檔案控制代碼之間變更檔案表示的方式。

|常式傳回的值|使用|
|-------------|---------|
|[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|將資料流與先前針對低層級 I/O 開啟的檔案建立關聯，並傳回此開啟資料流的指標。|
|[_fileno](../c-runtime-library/reference/fileno.md)|取得與資料流相關聯的檔案描述項。|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|傳回與現有 C 執行階段檔案描述項相關聯的作業系統檔案控制代碼|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|將現有作業系統檔案控制代碼與 C 執行階段檔案描述項建立關聯。|

 下列的 Win32 函式也會開啟檔案和管道：

- [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)

- [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)

- [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx) (CreateNamedPipe 函式)

## <a name="see-also"></a>請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
[目錄控制](../c-runtime-library/directory-control.md)<br/>
[系統呼叫](../c-runtime-library/system-calls.md)<br/>
