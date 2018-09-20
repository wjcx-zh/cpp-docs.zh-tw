---
title: 最佳化持續性和初始化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 395fc71f42dd947de331051233a5dcce086f7bb3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400805"
---
# <a name="optimizing-persistence-and-initialization"></a>最佳化持續性和初始化

根據預設，持續性和控制項中的初始化由處理`DoPropExchange`成員函式。 在一般的控制項中，此函式會包含數個呼叫**PX_** 函式 (`PX_Color`，`PX_Font`等等)，其中每一個屬性。

這種方法的優點是，單一`DoPropExchange`實作可用來初始化、 持續性; 在二進位格式，以及持續性; 在某些容器所使用的所謂 「 屬性包 」 格式。 這一個函式提供屬性和其預設值，在一個方便存取的位置中的所有資訊。

不過，這項通則的效率。 **PX_** 函式取得其透過多層式的實作原本就較少的彈性比更直接，但彈性更低，方法有效率。 此外，如果控制項傳遞至預設值**PX_** 函式，每次，即使在時的預設值可能不一定會使用的情況下必須提供預設值。 如果產生的預設值，重要的工作 （例如，當總值取自環境屬性），則額外不必要的工作是在不使用預設值的情況下。

您可以藉由覆寫您的控制項來改善您的控制項二進位的持續性效能`Serialize`函式。 此成員函式的預設實作會呼叫您`DoPropExchange`函式。 藉由覆寫它，您可以提供二進位的持續性的更直接實作。 例如，假設這`DoPropExchange`函式：

[!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

若要改善此控制項的二進位的持續性的效能，您可以覆寫`Serialize`函式，如下所示：

[!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion`本機變數可以用來偵測控制項的永續性狀態的版本要載入或儲存。 您可以使用這個變數，而不是呼叫[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)。

若要儲存極小空間中的永續性格式**BOOL**屬性 (並使其與所產生的格式相容`PX_Bool`)，您可以儲存為屬性**位元組**，如下：

[!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

請注意，在負載情況下，會使用暫存變數，則其值已指派，而不是轉型*m_boolProp*要**位元組**參考。 轉型技術可能會導致只有一個位元組的*m_boolProp*遭到修改，但未初始化的其餘位元組會保留。

在相同的控制項，您可以藉由覆寫最佳化控制項的初始化[COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) ，如下所示：

[!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

雖然`Serialize`並`OnResetState`已覆寫，`DoPropExchange`函式應該保持不變因為它仍然使用中的屬性包格式的持續性。 請務必維護這三個不論哪一個持續性機制，容器會使用這些函式以確保該控制項以一致的方式管理其屬性。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

