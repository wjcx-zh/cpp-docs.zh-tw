---
title: 最佳化持續性和初始化
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 57b98f7e2e4f9e23175b8b01c2e37ff49c499949
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624002"
---
# <a name="optimizing-persistence-and-initialization"></a>最佳化持續性和初始化

根據預設，控制項中的持續性和初始化會由成員函式來處理 `DoPropExchange` 。 在一般的控制項中，此函式包含對數個**PX_** 函式（ `PX_Color` 、 `PX_Font` 等）的呼叫，每個屬性各有一個函式。

這個方法有一個優點，就是 `DoPropExchange` 可以使用單一實作為初始化、保存二進位格式，以及在某些容器使用所謂的「屬性包」格式的持續性。 這個函式會在一個方便的位置，提供所有屬性及其預設值的相關資訊。

不過，這種一般性的代價是要付出更高的效率。 **PX_** 函式可透過多層式的實作為彈性，其本質上比更直接但較不具彈性的方法更有效率。 此外，如果控制項將預設值傳遞給**PX_** 函式，則每次都必須提供該預設值，即使是在預設值不一定要使用的情況下也一樣。 如果產生預設值是重要工作（例如，從環境屬性取得值時），則會在未使用預設值的情況下完成額外的非必要工作。

您可以藉由覆寫控制項的函式，來改善控制項的二進位持續性效能 `Serialize` 。 這個成員函式的預設實作用會呼叫您的函式 `DoPropExchange` 。 藉由覆寫它，您可以針對二進位持續性提供更直接的執行方式。 例如，請考慮 `DoPropExchange` 下列函數：

[!code-cpp[NVC_MFC_AxOpt#1](codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

若要改善這個控制項二進位持續性的效能，您可以覆寫函式，如下所示 `Serialize` ：

[!code-cpp[NVC_MFC_AxOpt#2](codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion`本機變數可用來偵測所載入或儲存之控制項的持續狀態版本。 您可以使用這個變數，而不是呼叫[CPropExchange：： GetVersion](reference/cpropexchange-class.md#getversion)。

若要以持續格式儲存**BOOL**屬性的少量空間（並讓它與所產生的格式相容 `PX_Bool` ），您可以將屬性儲存為**位元組**，如下所示：

[!code-cpp[NVC_MFC_AxOpt#3](codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

請注意，在載入案例中，會使用暫存變數，然後指派其值，而不是將*m_boolProp*轉換成**BYTE**參考。 轉型技術只會產生一個*m_boolProp*的一個位元組，並將剩餘的位元組保持未初始化。

針對相同的控制項，您可以覆寫[COleControl：： OnResetState](reference/colecontrol-class.md#onresetstate) ，以優化控制項的初始化，如下所示：

[!code-cpp[NVC_MFC_AxOpt#4](codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

雖然 `Serialize` 和已 `OnResetState` 被覆寫，但函 `DoPropExchange` 式應該保持不變，因為它仍然用於屬性包格式的持續性。 請務必維護這三個函式，以確保控制項一致地管理其屬性，而不論容器所使用的持續性機制為何。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項：最佳化](mfc-activex-controls-optimization.md)
