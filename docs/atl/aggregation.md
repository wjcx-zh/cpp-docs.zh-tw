---
title: 彙總
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 288af427bd6a8d9baf572dfad8e4a25452694ad9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491975"
---
# <a name="aggregation"></a>彙總

有時候, 物件的實作項會想要利用另一個預先建立的物件所提供的服務。 此外, 它也會讓第二個物件顯示為第一個的自然部分。 COM 透過內含專案和匯總達到這兩個目標。

「匯總」表示包含 (外部) 物件會在其建立程式中建立包含 (內部) 物件, 而內建物件的介面則是由外部公開。 物件允許本身可匯總。 如果是, 則必須遵循特定規則, 讓匯總正常運作。

主要是包含`IUnknown`物件上的所有方法呼叫都必須委派給包含物件。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[重複使用物件](/windows/win32/com/reusing-objects)
