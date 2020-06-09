---
title: 一階段和兩階段的物件建構
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 07e006d5b326486c54f23990c604a7d2ee0e4c83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625294"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>一階段和兩階段的物件建構

您可以選擇兩種方法來建立繪圖物件，例如畫筆和筆刷：

- *一個階段的結構*：在一個階段中，將物件進行結構化和初始化，全都使用此函式。

- *兩階段的結構*：在兩個不同的階段中，建立並初始化物件。 此函式會建立物件，而初始化函數會將其初始化。

兩階段的結構一律會更安全。 在一個階段的結構中，如果您提供不正確的引數或記憶體配置失敗，則此函式可能會擲回例外狀況。 這個問題是由兩個階段的結構所避免，不過您必須檢查是否有失敗。 不論是哪一種情況，終結物件都是相同的進程。

> [!NOTE]
> 這些技術適用于建立任何物件，而不只是繪圖物件。

## <a name="example-of-both-construction-techniques"></a>這兩種結構技術的範例

下列簡單的範例顯示兩種建立畫筆物件的方法：

[!code-cpp[NVC_MFCDocViewSDI#6](codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [繪圖物件](graphic-objects.md)

- [選取繪圖物件放入裝置內容中](selecting-a-graphic-object-into-a-device-context.md)

- [裝置內容](device-contexts.md)

- [在檢視中繪圖](drawing-in-a-view.md)

## <a name="see-also"></a>另請參閱

[圖形物件](graphic-objects.md)
