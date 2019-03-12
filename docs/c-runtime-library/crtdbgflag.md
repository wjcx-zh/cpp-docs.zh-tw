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
ms.openlocfilehash: a967b436d53acab6d76fa36fdf9b13c7c24d49c3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746978"
---
# <a name="crtdbgflag"></a>_CRTDBG_CHECK_CRT_DF

**_crtDbgFlag** 旗標包含五個位元欄位，可控制要追蹤、驗證、報告及傾印偵錯版本的堆積中多少記憶體。 旗標的位元欄位使用 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函式加以設定。 此旗標及其欄位會宣告於 Crtdbg.h 中。 只有當應用程式中已定義 [_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。

如需搭配其他偵錯函式使用此旗標的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="see-also"></a>另請參閱

[控制旗標](../c-runtime-library/control-flags.md)
