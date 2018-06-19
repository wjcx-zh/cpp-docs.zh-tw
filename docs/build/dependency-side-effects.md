---
title: 相依性的副作用 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7537e077a43318a487163d014b49d52cef66ce19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367520"
---
# <a name="dependency-side-effects"></a>相依性的副作用
如果您的目標指定不同的位置，在兩個相依性行中的冒號 （:） 和命令會顯示只是其中一條線之後，NMAKE 相鄰或結合時，就會解譯相依性。 它不會叫用任何命令，但反之會假設隸屬於一個描述區塊與執行的命令與其他相依性所指定的相依性的相依性的推斷規則。 例如，此設定的規則：  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
```  
  
 會評估為這個：  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 這個效果不會發生雙冒號 (`::`) 使用。 例如，此設定的規則：  
  
```Output  
bounce.exe :: jump.obj  
   echo Building bounce.exe...  
  
bounce.exe :: up.obj  
```  
  
 會評估為這個：  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
# invokes an inference rule  
```  
  
## <a name="see-also"></a>另請參閱  
 [目標](../build/targets.md)