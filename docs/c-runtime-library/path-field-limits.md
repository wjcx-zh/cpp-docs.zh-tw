---
title: "路徑欄位限制 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
dev_langs:
- C++
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e00104ada550d2510b031804d073098693144768
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="path-field-limits"></a>路徑欄位限制
## <a name="syntax"></a>語法  
  
```  
#include <stdlib.h>  
```  
  
## <a name="remarks"></a>備註  
 這些常數會定義路徑及路徑中個別欄位的最大長度。  
  
|常數|意義|  
|--------------|-------------|  
|`_MAX_DIR`|目錄元件的最大長度|  
|`_MAX_DRIVE`|磁碟機元件的最大長度|  
|`_MAX_EXT`|副檔名元件的最大長度|  
|`_MAX_FNAME`|檔案名稱元件的最大長度|  
|`_MAX_PATH`|完整路徑的最大長度|  
  
> [!NOTE]
>  C 執行階段支援的路徑長度最長為 32768 個字元，但是否支援此類較長路徑，則需取決於作業系統 (特別是檔案系統)。 欄位的總和不應超過 `_MAX_PATH`，以完整支援對 FAT32 檔案系統的回溯相容性。 [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)]、[!INCLUDE[WinXpFamily](../atl/reference/includes/winxpfamily_md.md)]、[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 和 Windows Vista NTFS 檔案系統支援的最長路徑長度為 32768 個字元，但只有在使用 Unicode API 時才支援此長度。 當使用長路徑名稱時，請在路徑前加上 \\\\?\ 字元，並使用 Unicode 版本的 C 執行階段函式。  
  
## <a name="see-also"></a>另請參閱  
 [全域常數](../c-runtime-library/global-constants.md)
