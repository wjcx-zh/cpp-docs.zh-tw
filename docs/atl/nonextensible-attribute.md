---
title: nonextensible 屬性
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: fda2a0d43144b6e9832e061e7198b3f3e65f8b86
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500106"
---
# <a name="nonextensible-attribute"></a>nonextensible 屬性

如果在執行時間不會延伸雙重介面 (也就是，您不會透過 `IDispatch::Invoke` vtable) 提供無法使用的方法或屬性，您應該將 **nonextensible** 屬性套用至您的介面定義。 這個屬性會將資訊提供給用戶端語言 (例如，可用來在編譯時期啟用完整程式碼驗證的 Visual Basic) 。 如果未提供此屬性，在執行時間之前，用戶端程式代碼中的 bug 可能仍會隱藏。

如需 **nonextensible** 屬性和範例的詳細資訊，請參閱 [nonextensible](../windows/attributes/nonextensible.md)。

## <a name="see-also"></a>另請參閱

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)
