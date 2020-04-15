---
title: 雙介面與事件
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 4ce5048c25bd55feb0f1eb20fc04ec6bfeead746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319610"
---
# <a name="dual-interfaces-and-events"></a>雙介面與事件

雖然可以將事件介面設計為雙介面,但有許多很好的設計理由不這樣做。 根本原因是事件的來源將僅通過 vtable`Invoke`或 通過 ()觸發事件,而不是兩者。 如果事件源將事件觸發為直接 vtable 方法調用`IDispatch`,則永遠不會使用這些方法,並且介面顯然應該是一個純 vtable 介面。 如果事件源將觸發事件作為調用`Invoke`,則永遠不會使用 vtable 方法,並且很明顯介面應該是一個介面。 如果將事件介面定義為雙,則需要客戶端實現永遠不會使用的介面的一部分。

> [!NOTE]
> 此參數通常不適用於雙介面。 從實現的角度來看,雙元是一種快速、方便且支援良好的實現介面的方法,這些介面可供各種用戶端訪問。

還有其他原因可以避免雙事件介面;無論是視覺基礎還是 Internet 資源管理員都支援它們。

## <a name="see-also"></a>另請參閱

[雙介面與 ATL](../atl/dual-interfaces-and-atl.md)
