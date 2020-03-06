---
title: RelogW
description: C++ BUILD Insights SDK RelogW 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 563b1aa92877ff5bc1216bc914c1c661de06dfc0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332695"
---
# <a name="relogw"></a>RelogW

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`RelogW` 函式是用來從 Windows 的輸入事件追蹤（ETW）追蹤中讀取 MSVC 事件，並將它們寫入新的、修改過的 ETW 追蹤。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE RelogW(
    const wchar_t*          inputLogFile,
    const wchar_t*          outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>參數

*inputLogFile*\
您想要從中讀取事件的輸入 ETW 追蹤。

*outputLogFile*\
要在其中寫入新事件的檔案。

*relogDescriptor*\
[RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md)物件的指標。 使用此物件來設定 relogging 會話。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

::: moniker-end
