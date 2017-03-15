---
title: "路徑欄位限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_MAX_EXT"
  - "_MAX_DIR"
  - "_MAX_PATH"
  - "_MAX_FNAME"
  - "_MAX_DRIVE"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_MAX_DIR 常數"
  - "_MAX_DRIVE 常數"
  - "_MAX_EXT 常數"
  - "_MAX_FNAME 常數"
  - "_MAX_PATH 常數"
  - "MAX_DIR 常數"
  - "MAX_DRIVE 常數"
  - "MAX_EXT 常數"
  - "MAX_FNAME 常數"
  - "路徑欄位常數"
  - "路徑, 最大限制"
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 路徑欄位限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
#include <stdlib.h>  
```  
  
## 備註  
 這些常數定義最大長度路徑以及在路徑中的個別欄位。  
  
|常數|意義|  
|--------|--------|  
|`_MAX_DIR`|目錄元件的最大長度。|  
|`_MAX_DRIVE`|磁碟機元件的最大長度|  
|`_MAX_EXT`|擴充元件的最大長度|  
|`_MAX_FNAME`|檔名元件的最大長度|  
|`_MAX_PATH`|完整路徑的最大長度|  
  
> [!NOTE]
>  C 執行階段支援路徑長度長至 32768 個字元；不過，它是由作業系統決定，尤其是檔案系統，來支援較長的路徑。  欄位的總和不能超過完整回溯相容性的 `_MAX_PATH` 和 FAT32 檔案系統。  [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)]、 [!INCLUDE[WinXpFamily](../c-runtime-library/includes/winxpfamily_md.md)]、 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]和 Windows Vista NTFS 檔案系統支援路徑是長度為 32768 個字元，不過，只有在使用 Unicode API\)。  當使用長路徑名稱時，前置\\ \\? \\字元在路徑並使用 C 執行階段函式的 Unicode 版本。  
  
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)