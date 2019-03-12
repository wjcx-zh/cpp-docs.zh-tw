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
ms.openlocfilehash: 8bcb0f5ea26218b74034eb0a41199a1104ba944d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739773"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

當應用程式的偵錯版本中定義了 **_CRTDBG_MAP_ALLOC** 旗標，堆積函式的基底版本就會直接對應至其偵錯版本。 旗標用在 Crtdbg.h 中以進行對應。 只有當應用程式中已定義 [_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。

如需使用堆積函式的偵錯版本與基底版本的詳細資訊，請參閱[使用偵錯版本與基底版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="see-also"></a>另請參閱

[控制旗標](../c-runtime-library/control-flags.md)
