---
title: 管理目前的檢視
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
ms.openlocfilehash: d2ce9d77234260ebcb1946dd381264fb6654a91c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621317"
---
# <a name="managing-the-current-view"></a>管理目前的檢視

在框架視窗的預設實作中，會持續記錄目前作用中的檢視。 如果框架視窗包含一個以上的檢視，例如在分割視窗中，目前的檢視就是最近使用中的檢視。 現用檢視表是獨立於 Windows 中的使用中視窗或目前的輸入焦點之外。

當使用中的 view 變更時，架構會呼叫其[OnActivateView](reference/cview-class.md#onactivateview)成員函式來通知目前的視圖。 您可以藉由檢查 `OnActivateView` 的*bActivate*參數來判斷要啟用或停用此視圖。 根據預設，`OnActivateView` 會在啟用時將焦點設定在目前的檢視。 當檢視停用或重新啟用時，您可以覆寫 `OnActivateView` 以執行任何特殊處理。 例如，您可能想要提供特殊視覺提示以區別現用檢視和其他非現用檢視。

框架視窗會將命令轉送至其目前的（使用中）視圖，如[命令路由](command-routing.md)中所述，做為標準命令路由的一部分。

## <a name="see-also"></a>另請參閱

[使用框架視窗](using-frame-windows.md)
