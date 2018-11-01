---
title: 初始化對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 2312a158835b28e7a17a6c30bb1fa148a63c07fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507961"
---
# <a name="initializing-the-dialog-box"></a>初始化對話方塊

之後的對話方塊方塊中，所有控制項都建立，但對話方塊之前 （一種類型） 的方塊會出現在畫面上，對話方塊物件的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)呼叫成員函式。 對於強制回應對話方塊，這會在 `DoModal` 期間發生。 對於非強制回應對話方塊方塊中，`OnInitDialog`時，會呼叫`Create`呼叫。 通常會覆寫 `OnInitDialog` 以初始化對話方塊的控制項，例如設定編輯方塊的初始文字。 您必須從您的 `OnInitDialog` 覆寫呼叫基底類別 `CDialog` 的 `OnInitDialog` 成員函式。

如果您想要設定對話方塊的背景色彩 （及其中的應用程式中所有其他對話方塊），請參閱[設定對話方塊的背景色彩](../mfc/setting-the-dialog-boxs-background-color.md)。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

