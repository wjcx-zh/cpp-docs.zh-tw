---
title: "目錄控制 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.programs
dev_langs: C++
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 74d0bd9011c77d67383e36b15817a71f853a409b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="directory-control"></a>目錄控制
這些常式會存取、修改和取得目錄結構的相關資訊。  
  
### <a name="directory-control-routines"></a>目錄控制常式  
  
|常式|用法|  
|-------------|---------|  
|[_chdir、_wchdir](../c-runtime-library/reference/chdir-wchdir.md)|變更目前工作目錄|  
|[_chdrive](../c-runtime-library/reference/chdrive.md)|變更目前的磁碟機|  
|[_getcwd、_wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|取得預設磁碟機的目前工作目錄|  
|[_getdcwd、_wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|取得指定磁碟機的目前工作目錄|  
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|使用磁碟機的資訊填入 `_diskfree_t` 結構。|  
|[_getdrive](../c-runtime-library/reference/getdrive.md)|取得目前 (預設) 的磁碟機|  
|[_getdrives](../c-runtime-library/reference/getdrives.md)|傳回代表目前可用之磁碟機的位元遮罩。|  
|[_mkdir、_wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|建立新的目錄|  
|[_rmdir、_wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|移除目錄|  
|[_searchenv、_wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md)、[_searchenv_s、_wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|在指定的路徑上搜尋指定的檔案|  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [檔案處理](../c-runtime-library/file-handling.md)   
 [系統呼叫](../c-runtime-library/system-calls.md)