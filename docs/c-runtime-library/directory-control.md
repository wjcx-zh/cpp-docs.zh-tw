---
title: 目錄控制 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c0ab24a55cddc13b743a28a022475b0c0b84e77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="directory-control"></a>目錄控制

這些常式會存取、修改和取得目錄結構的相關資訊。

## <a name="directory-control-routines"></a>目錄控制常式

|常式傳回的值|使用|
|-------------|---------|
|[_chdir、_wchdir](../c-runtime-library/reference/chdir-wchdir.md)|變更目前工作目錄|
|[_chdrive](../c-runtime-library/reference/chdrive.md)|變更目前的磁碟機|
|[_getcwd、_wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|取得預設磁碟機的目前工作目錄|
|[_getdcwd、_wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|取得指定磁碟機的目前工作目錄|
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|使用磁碟機的資訊填入 **_diskfree_t** 結構。|
|[_getdrive](../c-runtime-library/reference/getdrive.md)|取得目前 (預設) 的磁碟機|
|[_getdrives](../c-runtime-library/reference/getdrives.md)|傳回代表目前可用之磁碟機的位元遮罩。|
|[_mkdir、_wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|建立新的目錄|
|[_rmdir、_wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|移除目錄|
|[_searchenv、_wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md)、[_searchenv_s、_wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|在指定的路徑上搜尋指定的檔案|

## <a name="see-also"></a>請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [檔案處理](../c-runtime-library/file-handling.md)<br/>
 [系統呼叫](../c-runtime-library/system-calls.md)<br/>
