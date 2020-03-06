---
title: MSVC_TOOL_CODE 列舉
description: C++ BUILD Insights SDK MSVC_TOOL_CODE 列舉參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MSVC_TOOL_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d88a2227808867b04ef3b0557aee9c869beaead1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333668"
---
# <a name="msvc_tool_code-enum"></a>MSVC_TOOL_CODE 列舉

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`MSVC_TOOL_CODE` 列舉。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `MSVC_TOOL_CODE_CL` | 0（0x00000000） | 編譯器（cl .exe）。 |
| `MSVC_TOOL_CODE_LINK` | 1 (0x00000001) | 連結器（link .exe）。 |

## <a name="remarks"></a>備註

由 C SDK 函數使用。

::: moniker-end
