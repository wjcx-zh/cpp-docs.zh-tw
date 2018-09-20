---
title: 管理目前的檢視 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca9738f9b6083ef88c2f72e1608121f849f8e909
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425361"
---
# <a name="managing-the-current-view"></a>管理目前的檢視

在框架視窗的預設實作中，會持續記錄目前作用中的檢視。 如果框架視窗包含一個以上的檢視，例如在分割視窗中，目前的檢視就是最近使用中的檢視。 現用檢視表是獨立於 Windows 中的使用中視窗或目前的輸入焦點之外。

當現用檢視變更時，架構會通知目前的檢視，藉由呼叫其[OnActivateView](../mfc/reference/cview-class.md#onactivateview)成員函式。 您可以得知正在檢視是否啟用或停用檢查`OnActivateView`的*bActivate*參數。 根據預設，`OnActivateView` 會在啟用時將焦點設定在目前的檢視。 當檢視停用或重新啟用時，您可以覆寫 `OnActivateView` 以執行任何特殊處理。 例如，您可能想要提供特殊視覺提示以區別現用檢視和其他非現用檢視。

框架視窗會轉送命令，以其目前 （現用） 的檢視，如中所述[命令路由](../mfc/command-routing.md)，做為一部分的標準命令路由。

## <a name="see-also"></a>另請參閱

[使用框架視窗](../mfc/using-frame-windows.md)

