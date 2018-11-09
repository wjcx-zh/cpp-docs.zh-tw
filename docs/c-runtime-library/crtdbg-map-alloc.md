---
title: _CRTDBG_MAP_ALLOC
ms.date: 11/04/2016
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
ms.openlocfilehash: a6b6ca5d3e6fdc1bac43d082b0d7df5a87830050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453429"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

當應用程式的偵錯版本中定義了 **_CRTDBG_MAP_ALLOC** 旗標，堆積函式的基底版本就會直接對應至其偵錯版本。 旗標用在 Crtdbg.h 中以進行對應。 只有當應用程式中已定義 [_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。

如需使用堆積函式的偵錯版本與基底版本的詳細資訊，請參閱[使用偵錯版本與基底版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="see-also"></a>請參閱

[控制旗標](../c-runtime-library/control-flags.md)