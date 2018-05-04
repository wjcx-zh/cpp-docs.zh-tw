---
title: 巨集替換 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4028ee710cf38b6a4ef929de9a7e4ffad95f3e41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="macro-substitution"></a>巨集替換
當*巨集名稱*叫用時，每次發生*string1*其定義的字串會被取代*string2*。  
  
## <a name="syntax"></a>語法  
  
```  
$(macroname:string1=string2)  
```  
  
## <a name="remarks"></a>備註  
 巨集替換區分大小寫，是常值。*string1*和*string2*無法叫用巨集。 替代不會修改原始定義。 您可以取代文字中任何預先定義的巨集除了[ $$@ ](../build/filename-macros.md)。  
  
 沒有空格或定位點之前使用冒號。任何冒號後面都會解譯為常值。 如果*string2*是 null，所有出現的*string1*會刪除巨集的定義字串。  
  
## <a name="see-also"></a>另請參閱  
 [使用 NMAKE 巨集](../build/using-an-nmake-macro.md)