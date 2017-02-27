---
title: _CRTDBG_MAP_ALLOC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 709ba57e3cca392d2440c7ad528125dc31070cac

---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC
當應用程式的偵錯版本中定義了 **_CRTDBG_MAP_ALLOC** 旗標，堆積函式的基底版本就會直接對應至其偵錯版本。 旗標用在 Crtdbg.h 中以進行對應。 只有當應用程式中已定義 [_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。  
  
 如需使用堆積函式的偵錯版本與基底版本的詳細資訊，請參閱[使用偵錯版本與基底版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="see-also"></a>另請參閱  
 [控制旗標](../c-runtime-library/control-flags.md)


<!--HONumber=Feb17_HO4-->


