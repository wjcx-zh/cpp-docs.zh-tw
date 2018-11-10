---
title: 控制旗標
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 45349099ed5c607468430d2f0a901c6374d88fc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475734"
---
# <a name="control-flags"></a>控制旗標

Microsoft C 執行階段程式庫的偵錯版本使用下列旗標控制堆積配置和報告處理序。 如需詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。

|旗標|描述|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|將基底堆積函式對應到其偵錯版本對應項|
|[_DEBUG](../c-runtime-library/debug.md)|可讓您使用執行階段函式的偵錯版本|
|[_CRTDBG_CHECK_CRT_DF](../c-runtime-library/crtdbgflag.md)|控制偵錯堆積管理員如何追蹤配置|

這些旗標可以使用 /D 命令列選項或 `#define` 指示詞定義。 當旗標使用 `#define` 定義時，指示詞必須在常式宣告的標頭檔 include 陳述式之前出現。

## <a name="see-also"></a>請參閱

[全域變數和標準類型](../c-runtime-library/global-variables-and-standard-types.md)