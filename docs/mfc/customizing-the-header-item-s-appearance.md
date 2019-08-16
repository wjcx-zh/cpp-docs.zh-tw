---
title: 自訂標題專案&#39;的外觀
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 6ce676695d717fcc5d418fe4ed5df91b4f9bca95
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508713"
---
# <a name="customizing-the-header-item39s-appearance"></a>自訂標題專案&#39;的外觀

藉由在您第一次建立標題控制項 ([CHeaderCtrl:: create](../mfc/reference/cheaderctrl-class.md#create)) 時設定*dwStyle*參數, 您可以定義標頭專案或標頭控制項本身的外觀和行為。

以下是可設定之樣式的示範及其用途：

- 若要讓標題專案看起來像是按鍵, 請使用**HDS_BUTTONS**樣式。

   如果您要執行動作來回應標題項目上的滑鼠點選作業，例如 Microsoft Outlook 中以特定欄排序資料，請使用這個樣式。

- 若要在滑鼠游標傳入標頭專案時, 將「熱追蹤」外觀提供給它們, 請使用**HDS_HOTTRACK**樣式。

   熱追蹤會在平面的標題列上，於指標通過項目時顯示 3D 外框。

- 若要指出標題控制項應隱藏, 請使用**HDS_HIDDEN**樣式。

   **HDS_HIDDEN**樣式表示標題控制項要當做資料容器使用, 而不是視覺化控制項。 這個樣式不會自動隱藏控制項，而是會影響 `CHeaderCtrl::Layout` 的行為。 在`WINDOWPOS`結構的*cy*成員中傳回的值會是零, 表示使用者看不到該控制項。

如需這些屬性的詳細資訊, 請參閱 Windows SDK 中的[專案](/windows/win32/Controls/header-controls)。 如需將專案加入至標題控制項的詳細資訊, 請參閱[將專案加入至標題控制項](../mfc/adding-items-to-the-header-control.md)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
