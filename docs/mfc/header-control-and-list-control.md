---
title: 標題控制項和清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: f9dd34b27ddbdc0b99fafbb23ad1cf9782d98605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626411"
---
# <a name="header-control-and-list-control"></a>標題控制項和清單控制項

在大部分的情況下，您會使用內嵌在[CListCtrl](reference/clistctrl-class.md)或[CListView](reference/clistview-class.md)物件中的標題控制項。 不過，在某些情況下，會需要個別的標題控制項物件，例如在[CView](reference/cview-class.md)衍生的物件中運算元據（以欄位或資料列排列）。 在這些情況下，您需要更充分掌控內嵌標題控制項的外觀和預設行為。

在您想要讓標題控制項提供標準的預設行為的常見情況下，您可能會想要改為使用[CListCtrl](reference/clistctrl-class.md)或[CListView](reference/clistview-class.md) 。 `CListCtrl`當您想要預設標題控制項的功能（內嵌在清單視圖通用控制項中）時，請使用。 當您想要將預設標題控制項的功能內嵌在 view 物件中時，請使用[CListView](reference/clistview-class.md) 。

> [!NOTE]
> 如果使用**LVS_REPORT**樣式建立清單視圖控制項，這些控制項只會包含內建標題控制項。

在大部分的情況下，可以藉由變更包含清單視圖控制項的樣式來修改內嵌標題控制項的外觀。 此外，您也可以透過父清單視圖控制項的成員函式來取得標題控制項的相關資訊。 不過，針對內嵌標題控制項的屬性和樣式，若要進行完整的控制和存取，建議您取得標頭控制項物件的指標。

內嵌的標頭控制項物件可以從 `CListCtrl` 或 `CListView` 呼叫個別類別的成員函式來存取 `GetHeaderCtrl` 。 下列程式碼將示範此作業：

[!code-cpp[NVC_MFCControlLadenDialog#14](codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [搭配使用影像清單與標題控制項](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](using-cheaderctrl.md)<br/>
[控制項](controls-mfc.md)
