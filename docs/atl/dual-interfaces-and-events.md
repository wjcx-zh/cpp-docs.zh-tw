---
title: 雙重介面和事件
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: f94e87f077846af8d61b06145f776f385051e79f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640592"
---
# <a name="dual-interfaces-and-events"></a>雙重介面和事件

雖然您可以設計成雙重事件介面，有幾個良好的設計的理由，不能這麼做。 基本的原因是事件來源只會引發事件，透過 vtable 或`Invoke`，不能同時。 如果事件來源，就會引發事件以直接的 vtable 方法呼叫，`IDispatch`絕不會使用方法以及很顯然介面應該是純粹的 vtable 介面。 如果事件來源就會引發事件的呼叫為`Invoke`，絕不會使用 vtable 方法，且為清除介面已被分配介面。 如果您為雙重介面定義事件介面，您將會要求用戶端實作絕不會使用介面的一部分。

> [!NOTE]
>  這個引數不適用於雙重介面，在一般情況下。 從實作觀點來看，雙重介面是快速、 方便，且受到多方支援的方式實作各種不同的用戶端存取的介面。

還有其他理由來避免雙重的事件介面;Visual Basic 和 Internet Explorer 都不支援這些選項。

## <a name="see-also"></a>另請參閱

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)

