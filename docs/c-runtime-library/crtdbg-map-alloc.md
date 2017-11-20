---
title: _CRTDBG_MAP_ALLOC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs: C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2b61b315baa337675147ded1232a943e82b24ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC
當應用程式的偵錯版本中定義了 **_CRTDBG_MAP_ALLOC** 旗標，堆積函式的基底版本就會直接對應至其偵錯版本。 旗標用在 Crtdbg.h 中以進行對應。 只有當應用程式中已定義 [_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。  
  
 如需使用堆積函式的偵錯版本與基底版本的詳細資訊，請參閱[使用偵錯版本與基底版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="see-also"></a>另請參閱  
 [控制旗標](../c-runtime-library/control-flags.md)