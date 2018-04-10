---
title: 定義巨集的位置 |Microsoft 文件
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
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2e646de4cf67fc249d69fb07789f4c8a3e14bf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="where-to-define-macros"></a>定義巨集的位置
命令列、 指令檔、 makefile 或 Tools.ini 檔案中定義巨集。  
  
 Makefile 或 Tools.ini 檔中，每個巨集定義必須出現在不同行，而且不得以空格或定位鍵。會忽略空格或等號前後的索引標籤。 所有[字元的字串](../build/defining-an-nmake-macro.md)是常值，包括周圍的引號和內嵌的空格。  
  
 在命令列或命令檔中，空格和定位點分隔的引數，不可以出現在等號。 如果`string`有內嵌空格或定位點，以雙引號括住字串本身或整個巨集 ("")。  
  
## <a name="see-also"></a>請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)