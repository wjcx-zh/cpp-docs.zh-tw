---
title: "巨集替換 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c2ea7a2509e58cfd4da163cc76c018d06c244fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [使用 NMAKE 巨集](../build/using-an-nmake-macro.md)