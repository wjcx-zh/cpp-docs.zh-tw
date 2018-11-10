---
title: _CRTDBG_CHECK_CRT_DF
ms.date: 11/04/2016
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
ms.openlocfilehash: 5abb0418b5ffb1f95bf7b362f621f99f411094d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435291"
---
# <a name="crtdbgflag"></a>_CRTDBG_CHECK_CRT_DF

**_crtDbgFlag** 旗標包含五個位元欄位，可控制要追蹤、驗證、報告及傾印偵錯版本的堆積中多少記憶體。 旗標的位元欄位使用 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函式加以設定。 此旗標及其欄位會宣告於 Crtdbg.h 中。 只有當應用程式中已定義 [_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。

如需搭配其他偵錯函式使用此旗標的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="see-also"></a>請參閱

[控制旗標](../c-runtime-library/control-flags.md)