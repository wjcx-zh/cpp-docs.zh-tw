---
title: 關閉可見時啟動選項
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: 42dbec7a55085235e43fa14ab6406bfb3526afdb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464827"
---
# <a name="turning-off-the-activate-when-visible-option"></a>關閉可見時啟動選項

控制項有兩種基本的狀態： 作用中和非使用中。 傳統上，這些狀態已由控制項是否具有視窗來辨別。 作用中的控制項有視窗;非現用控制項不提供支援。 推出的無視窗啟用之後，這項區別不再是通用的但仍適用於許多控制項。

比較 ActiveX 控制項通常會執行初始化的其餘部分，建立視窗是非常耗費資源的作業。 在理想狀況下，控制項會延後建立其視窗，除非有絕對必要性。

在容器中一直都可看到許多控制項，但不一定要使用這些控制項。 通常，控制項會保持在非現用狀態，直到使用者執行操作要求它成為使用中 (例如按一下滑鼠或按下 TAB 鍵)。 若要使控制項維持非使用中，直到容器需要啟動它，移除**OLEMISC_ACTIVATEWHENVISIBLE**從控制項的其他旗標的旗標：

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

**OLEMISC_ACTIVATEWHENVISIBLE**如果您關閉旗標會自動省略**可見時啟動**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX 頁面當您建立您的控制項時，就會控制精靈。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

