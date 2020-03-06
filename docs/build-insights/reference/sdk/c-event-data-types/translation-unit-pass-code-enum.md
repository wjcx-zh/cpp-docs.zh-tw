---
title: TRANSLATION_UNIT_PASS_CODE 列舉
description: C++ BUILD Insights SDK TRANSLATION_UNIT_PASS_CODE 列舉參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1219eed98fd01e8c91d8750977e2d8ca4498d649
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333577"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE 列舉

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`TRANSLATION_UNIT_PASS_CODE` 列舉。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0（0x00000000） | 前端階段，負責剖析原始程式碼並將它轉換成中繼語言。 |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | 後端階段，負責優化中繼語言並將它轉換成機器碼。 |

## <a name="remarks"></a>備註

由 C SDK 函數使用。

::: moniker-end
