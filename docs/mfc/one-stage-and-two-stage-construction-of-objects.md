---
title: 一階段和兩階段的物件建構
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 8f221ac6b63a06c65f932a695dfbf7b93ae7ac96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375973"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>一階段和兩階段的物件建構

您可以選擇兩種建立圖形物件的技術,如筆和畫筆:

- *一階段建構*:在一個階段建構和初始化物件,全部使用構造函數。

- *兩階段構造*:分兩個階段構造和初始化物件。 建構函數創建物件,初始化函數將初始化。

兩階段結構始終更安全。 在一階段構造中,如果提供不正確的參數或記憶體分配失敗,構造函數可能會引發異常。 此問題可以通過兩階段構造避免,儘管您必須檢查故障。 在這兩種情況下,銷毀物件都是相同的過程。

> [!NOTE]
> 這些技術適用於創建任何物件,而不僅僅是圖形物件。

## <a name="example-of-both-construction-techniques"></a>兩種施工技術範例

下面的簡短示例顯示了建構筆物件的兩種方法:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [圖形物件](../mfc/graphic-objects.md)

- [在裝置中選擇圖形物件](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [裝置內容](../mfc/device-contexts.md)

- [在檢視中繪圖](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>另請參閱

[圖形物件](../mfc/graphic-objects.md)
