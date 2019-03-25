---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: f9c8de7c8686b89a2ab9570a2558e3f649e545b5
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58419080"
---
# <a name="allocator"></a>allocator

**Microsoft 專屬**

**Allocator**宣告規範可以套用至要顯示透過事件追蹤的 Windows (ETW) 配置的自訂記憶體配置函式。

## <a name="syntax"></a>語法

```
   __declspec(allocator) 
```

## <a name="remarks"></a>備註

在 Visual Studio 中的原生記憶體分析工具的運作方式是收集配置在執行階段所發出的 ETW 事件資料。 在來源層級已註釋 CRT 和 Windows SDK 中的配置器，以便擷取其配置資料。 如果您正在撰寫自己的配置器，則傳回新配置的堆積記憶體的指標的任何函式可以使用裝飾`__declspec(allocator)`如 myMalloc 本範例所示：

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

如需詳細資訊，請參閱 <<c0> [ 量值 Visual Studio 中的記憶體使用量](/visualstudio/profiling/memory-usage)並[自訂原生 ETW 堆積事件](/visualstudio/profiling/custom-native-etw-heap-events)。