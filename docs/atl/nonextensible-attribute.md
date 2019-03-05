---
title: nonextensible 屬性
ms.date: 11/04/2016
f1_keywords:
- nonextensible
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5aa5b8514435e9876500daa4d92504d75eb6dc23
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257627"
---
# <a name="nonextensible-attribute"></a>nonextensible 屬性

如果將不在執行階段擴充的雙重介面 (也就是您將不會提供方法或屬性，透過`IDispatch::Invoke`不是可透過 vtable)，您應該套用**nonextensible**屬性至您的介面定義。 此屬性會提供可用來啟用完整的程式碼在編譯時期的驗證的用戶端語言 （例如 Visual Basic) 的資訊。 如果未提供這個屬性，bug 可能會維持在用戶端程式碼中隱藏執行階段。

如需詳細資訊**nonextensible**屬性和範例，請參閱[nonextensible](../windows/nonextensible.md)。

## <a name="see-also"></a>另請參閱

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)
