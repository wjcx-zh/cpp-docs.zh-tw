---
title: "定義規則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0d6ca616e3685db36d6d24b339a860eab4c6150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [推斷規則](../build/inference-rules.md)