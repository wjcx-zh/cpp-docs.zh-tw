---
title: 一階段和兩階段的物件建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6454e34830591eccb2b696948d02f74ad8cebfd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426571"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>一階段和兩階段的物件建構

您可以建立畫筆和筆刷等圖形物件的兩個技術之間選擇：

- *一階段建構*： 建構和初始化此物件在一個階段中，都可以透過建構函式。

- *兩階段建構*： 建構和初始化物件的兩個不同的階段。 建構函式會建立物件，並初始化函式加以初始化。

兩階段建構永遠是更安全的。 一階段建構中建構函式可能擲回例外狀況，如果您提供不正確的引數或記憶體配置失敗。 透過兩階段建構，避免這個問題，雖然您需要檢查有錯誤。 在任一情況下，終止此物件是相同的程序。

> [!NOTE]
>  這些技術適用於建立任何物件，不只是圖形的物件。

## <a name="example-of-both-construction-techniques"></a>這兩種建構技巧的範例

下列簡短的範例顯示建構一個 pen 物件的兩種方法：

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [圖形物件](../mfc/graphic-objects.md)

- [選取圖形物件放入裝置內容](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [裝置內容](../mfc/device-contexts.md)

- [在檢視中繪圖](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>另請參閱

[圖形物件](../mfc/graphic-objects.md)

