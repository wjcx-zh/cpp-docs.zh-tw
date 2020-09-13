---
title: TEMPLATE_INSTANTIATION_DATA 結構
description: C + + Build Insights SDK TEMPLATE_INSTANTIATION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 15bbb25c3abac339201179e763bffd916dba0480
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040869"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`TEMPLATE_INSTANTIATION_DATA`結構描述範本具現化。

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

| 名稱 | 描述 |
|--|--|
| `SpecializationSymbolKey` | 範本特製化類型的索引鍵。 這個值在要分析的追蹤內是唯一的。 |
| `PrimaryTemplateSymbolKey` | 特製化之主要範本類型的索引鍵。 這個值在要分析的追蹤內是唯一的。 |
| `KindCode` | 範本具現化的類型。 如需詳細資訊，請參閱 [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md)。 |

## <a name="remarks"></a>備註

結構中的索引鍵在所 `TEMPLATE_INSTANTIATION_DATA` 分析的追蹤內是唯一的。 不過，來自不同編譯器前端傳遞的兩個不同金鑰可能會指向兩個相同的類型。 `TEMPLATE_INSTANTIATION_DATA`使用多個編譯器前端傳遞的資訊時，請使用[SYMBOL_NAME](../event-table.md#symbol-name)事件來判斷兩個類型是否相同。 `SymbolName` 在完成所有範本具現化之後，會在編譯器前端傳遞結束時發出事件。

::: moniker-end
