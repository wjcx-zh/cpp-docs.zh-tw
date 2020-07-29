---
title: 使用偵錯版檢查記憶體覆寫
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 152f72749d2ebdacd46dd3e4db671bc5705d4b6a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213745"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>使用偵錯版檢查記憶體覆寫

若要使用 debug 組建來檢查記憶體覆寫，您必須先重建您的專案以進行 debug。 然後，移至應用程式函式的開頭， `InitInstance` 並新增下列這一行：

```
afxMemDF |= checkAlwaysMemDF;
```

「調試記憶體配置器」會將防護位元組放在所有記憶體配置的周圍。 不過，除非您檢查是否已變更（這會指出記憶體的覆寫），否則這些防護位元組不會執行任何良好的處理。 否則，這只會提供緩衝區，事實上，您可以讓您擺脫記憶體的覆寫。

藉由開啟 `checkAlwaysMemDF` ，您會在 `AfxCheckMemory` 每次呼叫 **`new`** 或時，強制 MFC 呼叫函數 **`delete`** 。 如果偵測到記憶體覆寫，它會產生類似下面的追蹤訊息：

```
Damage Occurred! Block=0x5533
```

如果您看到其中一個訊息，您必須逐步執行您的程式碼，以判斷發生損毀的位置。 若要更精確地隔離發生記憶體覆寫的位置，您可以對自己進行明確的呼叫 `AfxCheckMemory` 。 例如：

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

如果第一個判斷提示成功，而第二個判斷提示失敗，則表示記憶體覆寫必須在這兩個呼叫之間的函式中發生。

視應用程式的本質而定，您可能會發現 `afxMemDF` 程式的執行速度太慢而無法進行測試。 `afxMemDF`變數會導致在 `AfxCheckMemory` 每次呼叫 new 和 delete 時呼叫。 在這種情況下，您應該散佈自己對 `AfxCheckMemory` （）的呼叫，如上所示，並嘗試隔離記憶體覆寫。

## <a name="see-also"></a>另請參閱

[修正發行組建問題](fixing-release-build-problems.md)
