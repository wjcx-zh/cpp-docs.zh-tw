---
title: 檔名巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2073e4fcb365b3beb10d4040c0f54d9f61a0431
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="filename-macros"></a>檔名巨集
檔名巨集是預先定義為相依性 （在磁碟上的不完整的檔名規格） 中指定的檔名。 這些巨集不需要括在括號時叫用。指定只是 $ 所示。  
  
|巨集|意義|  
|-----------|-------------|  
|**$@**|目前目標的完整名稱 （路徑、 基底名稱、 副檔名），如目前所指定。|  
|**$$@**|目前目標的完整名稱 （路徑、 基底名稱、 副檔名），如目前所指定。 只做為相依性的相依性中有效。|  
|**$\***|目前目標的路徑和基底名稱不包含副檔名。|  
|**$\*\***|目前目標的所有相依項目。|  
|**$?**|時間戳記晚於目前的目標使用的所有相依項目。|  
|**$<**|時間戳記晚於目前目標的相依檔案。 只有在推斷規則中的命令有效。|  
  
 若要指定預先定義的檔案名稱巨集的一部份，附加巨集修飾詞和括號括住的已修改的巨集。  
  
|修飾詞|產生的檔案名稱部分|  
|--------------|-----------------------------|  
|**D**|磁碟機和目錄|  
|**B**|基底名稱|  
|**F**|基底名稱再加上副檔名|  
|**R**|磁碟機加上目錄加上的基底名稱|  
  
## <a name="see-also"></a>請參閱  
 [特殊的 NMAKE 巨集](../build/special-nmake-macros.md)