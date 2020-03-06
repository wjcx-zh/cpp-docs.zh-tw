---
title: TEMPLATE_INSTANTIATION_DATA 結構
description: C++ BUILD Insights SDK TEMPLATE_INSTANTIATION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333619"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`TEMPLATE_INSTANTIATION_DATA` 結構描述範本具現化。

## <a name="syntax"></a>語法

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `SpecializationSymbolKey` | 範本特製化類型的索引鍵。 這個值在要分析的追蹤內是唯一的。 |
| `PrimaryTemplateSymbolKey` | 特製化之主要範本類型的索引鍵。 這個值在要分析的追蹤內是唯一的。 |
| `KindCode` | 範本具現化的類型。 如需詳細資訊，請參閱[TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md)。 |

## <a name="remarks"></a>備註

在要分析的追蹤內，`TEMPLATE_INSTANTIATION_DATA` 結構中的索引鍵是唯一的。 不過，來自不同編譯器前端傳遞的兩個不同索引鍵可能會指向兩個相同的類型。 從多個編譯器前端傳遞 `TEMPLATE_INSTANTIATION_DATA` 資訊時，請使用[SYMBOL_NAME](../event-table.md#symbol-name)事件來判斷兩個類型是否相同。 執行所有範本具現化之後，會在編譯器前端階段結束時發出 `SymbolName` 事件。

::: moniker-end
