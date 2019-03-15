---
title: 使用偵錯版檢查記憶體覆寫
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824859"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>使用偵錯版檢查記憶體覆寫

若要使用偵錯組建檢查記憶體覆寫，您必須先重建您的專案進行偵錯。 然後，移至您的應用程式的最開頭`InitInstance`函式，並新增下面這一行：

```
afxMemDF |= checkAlwaysMemDF;
```

偵錯記憶體配置器會將所有記憶體配置周圍的保護位元組。 不過，這些保護位元組並沒有任何效用，除非您檢查是否已經變更 （這會指示記憶體覆寫）。 否則，這只是提供的緩衝區，事實上，可能會讓您擺脫這個記憶體覆寫。

藉由開啟`checkAlwaysMemDF`，您將會強制進行呼叫的 MFC`AfxCheckMemory`函式每次呼叫**新**或是**刪除**進行。 偵測到記憶體覆寫時，它會產生追蹤訊息看起來如下所示：

```
Damage Occurred! Block=0x5533
```

如果您看到其中一個訊息，您需要逐步執行程式碼，以判斷發生損毀。 若要找出更精確地記憶體覆寫發生的位置，您可以進行明確呼叫`AfxCheckMemory`自己。 例如: 

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

如果成功，第一次的判斷提示，而第二個失敗，這表示，必須有記憶體覆寫發生在兩個呼叫之間的函式。

根據您的應用程式的本質，您可能會發現`afxMemDF`會導致您的程式執行速度太慢，即使測試。 `afxMemDF`變數會造成`AfxCheckMemory`針對至新增的每次呼叫呼叫，並刪除。 在此情況下，您應該散佈到呼叫`AfxCheckMemory`（），如上所示，然後嘗試找出記憶體覆寫該方法。

## <a name="see-also"></a>另請參閱

[解決發行組建的問題](fixing-release-build-problems.md)
