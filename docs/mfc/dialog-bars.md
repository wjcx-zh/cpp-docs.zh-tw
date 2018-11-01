---
title: 對話方塊列
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: 3a3276e9b5d0e1ab8d8e77fae983d24ff1e4b4e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557391"
---
# <a name="dialog-bars"></a>對話方塊列

對話方塊列是工具列、 一種的[控制列](../mfc/control-bars.md)可包含任何類型的控制項。 因為它具有非強制回應對話方塊的特性[CDialogBar](../mfc/reference/cdialogbar-class.md)物件提供更為強大的工具列。

工具列和 `CDialogBar` 物件之間有幾項主要差異。 `CDialogBar` 物件會從對話方塊樣板資源建立，您可以使用 Visual C++ 對話方塊編輯器建立該資源，並且該資源可以包含任何類型的 Windows 控制項。 使用者可以使用 Tab 鍵在控制項之間移動。 您也可以指定對齊樣式將對話方塊列與父框架視窗的任何部分對齊，或者甚至如果重新調整父框架視窗的大小，也可使其留在原位置。 下圖顯示含有各種控制項的對話方塊列。

![VC 對話方塊列](../mfc/media/vc378t1.gif "vc378t1")對話方塊列

而在其他方面，使用 `CDialogBar` 物件就和使用非強制回應對話方塊一樣。 使用對話方塊編輯器來設計和建立對話方塊資源。

對話方塊列的其中一項優點是它們可以包含控制項而非按鈕。

當其正常從 `CDialog` 衍生您自己的對話方塊類別時，您通常不會為對話方塊列衍生您自己的類別。 對話方塊列是主視窗和任何對話方塊列控制項通知訊息，擴充功能，例如**BN_CLICKED**或是**EN_CHANGE**，將會傳送到對話方塊列的主視窗的父代。

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)<br/>
[範例](../visual-cpp-samples.md)

