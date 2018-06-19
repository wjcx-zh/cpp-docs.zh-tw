---
title: 多個目標 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c1e072b5c831cecabaf1fd63034a0746b3e3419
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368183"
---
# <a name="multiple-targets"></a>多重目標
NMAKE 評估成單一的相依性的多個目標為不同的描述區塊中所指定的每個。  
  
 例如，這個...  
  
```Output  
bounce.exe leap.exe : jump.obj  
   echo Building...  
```  
  
 ..來評估如下：  
  
```Output  
bounce.exe : jump.obj  
   echo Building...  
leap.exe : jump.obj  
   echo Building...  
```  
  
## <a name="see-also"></a>另請參閱  
 [目標](../build/targets.md)