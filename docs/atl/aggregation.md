---
title: 彙總
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 2eec7a801f9fe16bc48fc888d10ce413ec7e79db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223502"
---
# <a name="aggregation"></a>彙總

有些的時候，當物件的實作項想要充分利用預先建置的另一個物件所提供的服務。 此外，它想要這個第二個物件顯示的第一個自然的一部分。 COM 可完成這兩個透過內含項目和彙總目標。

彙總表示包含 （外部） 的物件會包含 （內部） 的物件建立做為其建立程序的一部分，而且由外部公開內部物件的介面。 物件可讓本身可以彙總。 如果是，它必須遵循特定規則才能正常運作的彙總。

所有主要`IUnknown`所包含的物件上的方法呼叫必須委派給包含的物件。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[重複使用的物件](/windows/desktop/com/reusing-objects)
