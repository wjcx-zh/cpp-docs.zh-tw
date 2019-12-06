---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 2e2615829f6491bf660859fbc86ebcd07a56c5fe
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857680"
---
# <a name="allocator"></a>allocator

**Microsoft 專屬**

配置器宣告規範可以套用至自訂記憶體配置函式，以透過 Windows 事件追蹤（ETW）顯示配置。

## <a name="syntax"></a>語法

```
   __declspec(allocator) 
```

## <a name="remarks"></a>備註

Visual Studio 中的原生記憶體分析工具的運作方式，是收集在執行時間期間發出的配置 ETW 事件資料。 在來源層級已註釋 CRT 和 Windows SDK 中的配置器，以便擷取其配置資料。 如果您要撰寫自己的配置器，則傳回新配置堆積記憶體之指標的任何函式都可以使用 `__declspec(allocator)`裝飾，如下列 Mymalloc 所示範例所示：

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

如需詳細資訊，請參閱[測量 Visual Studio 中的記憶體使用量](/visualstudio/profiling/memory-usage)和[自訂的原生 ETW 堆積事件](/visualstudio/profiling/custom-native-etw-heap-events)。

**結束 Microsoft 專屬**
