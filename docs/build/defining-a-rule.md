---
title: 定義規則 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8ff7c58033ac5f7e42764d185c45c206bf406f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="defining-a-rule"></a>定義規則
*Fromext*代表相依的檔案，副檔名和*toext*代表目標檔案的副檔名。  
  
```  
.fromext.toext:  
   commands  
```  
  
## <a name="remarks"></a>備註  
 副檔名不區分大小寫。 巨集可以叫用來代表*fromext*和*toext*; 巨集展開期間前置處理。 句號 （.） 前面*fromext*必須出現在一行的開頭。 冒號 （:） 被加上零或多個空格或定位點。 它後面只能由空格或定位點、 分號 （;），指定的命令、 指定註解，數字符號 （#） 或新行字元。 不允許使用任何其他空格。 描述區塊中指定的命令。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [在規則中的搜尋路徑](../build/search-paths-in-rules.md)  
  
## <a name="see-also"></a>另請參閱  
 [推斷規則](../build/inference-rules.md)