---
title: TRANSLATION_UNIT_PASS_CODE枚舉
description: C++生成見解 SDK TRANSLATION_UNIT_PASS_CODE枚舉引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0162d7e53bb7ee7035b94a6b640f6db87cd8b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325294"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE枚舉

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`TRANSLATION_UNIT_PASS_CODE`舉。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x000000) | 前端傳遞,負責分析原始程式碼並將其轉換為中間語言。 |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | 後端通,負責優化中間語言並將其轉換為機器代碼。 |

## <a name="remarks"></a>備註

由 C SDK 函數使用。

::: moniker-end
