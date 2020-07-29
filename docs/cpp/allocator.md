---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: a26cf4d2b79d64ddc9f0b60982d778e33d0f200a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216644"
---
# `allocator`

**Microsoft 特定的**

宣告 **`allocator`** 規範可以套用至自訂記憶體配置函式，以透過 Windows 事件追蹤（ETW）顯示配置。

## <a name="syntax"></a>語法

> **`__declspec(allocator)`**

## <a name="remarks"></a>備註

Visual Studio 中的原生記憶體分析工具的運作方式，是收集在執行時間期間發出的配置 ETW 事件資料。 在來源層級已註釋 CRT 和 Windows SDK 中的配置器，以便擷取其配置資料。 如果您要撰寫自己的配置器，則傳回新配置堆積記憶體之指標的任何函式都可以使用裝飾 `__declspec(allocator)` ，如下列 mymalloc 所示範例所示：

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

如需詳細資訊，請參閱[測量 Visual Studio 中的記憶體使用量](/visualstudio/profiling/memory-usage)和[自訂的原生 ETW 堆積事件](/visualstudio/profiling/custom-native-etw-heap-events)。

**結束 Microsoft 專有**
