---
title: 雷洛加
description: C++生成見解 SDK 重新登錄函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5a772b1156fc69eeef39514afe401c549c3b7c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323840"
---
# <a name="reloga"></a>雷洛加

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`RelogA`函數用於從 Windows (ETW) 追蹤的事件追蹤讀取 MSVC 事件,並將它們寫入新的修改後的 ETW 追蹤中。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>參數

*輸入紀錄檔*\
要從中讀取事件的輸入 ETW 跟蹤。

*輸出記錄檔*\
寫入新事件的檔。

*重記錄符*\
指向[RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md)物件的指標。 使用此物件設定重新記錄工作階段。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

::: moniker-end
