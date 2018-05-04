---
title: 定義 NMAKE 巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5997eee052ebba198e1fb52da35322c65a32627b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="defining-an-nmake-macro"></a>定義 NMAKE 巨集
## <a name="syntax"></a>語法  
  
```  
  
macroname=string  
```  
  
## <a name="remarks"></a>備註  
 *巨集名稱*是字母、 數字和最多 1024 個字元、 底線 (_) 的組合，是區分大小寫。 *巨集名稱*可以包含已叫用的巨集。 如果*巨集名稱*包含所叫用巨集的叫用的巨集，不可為 null 或未定義。  
  
 `string`可以是任何字元零或多個序列。 Null 字串，包含零個字元或只有空格或定位字元。 `string`可以包含巨集引動過程。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [在巨集中的特殊字元](../build/special-characters-in-macros.md)  
  
 [Null 和未定義的巨集](../build/null-and-undefined-macros.md)  
  
 [定義巨集的位置](../build/where-to-define-macros.md)  
  
 [巨集定義的優先順序](../build/precedence-in-macro-definitions.md)  
  
## <a name="see-also"></a>另請參閱  
 [巨集和 NMAKE](../build/macros-and-nmake.md)