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
ms.openlocfilehash: 1f8f8f7e40b1c873c4428542c628d02e250f14b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626344"
---
# <a name="initializing-the-dialog-box"></a>初始化對話方塊

在對話方塊和其所有控制項都建立之後，但在畫面上顯示對話方塊（屬於任一類型）之前，會呼叫對話方塊物件的[OnInitDialog](reference/cdialog-class.md#oninitdialog)成員函式。 對於強制回應對話方塊，這會在 `DoModal` 期間發生。 若為非強制回應對話方塊， `OnInitDialog` 則會在 `Create` 呼叫時呼叫。 通常會覆寫 `OnInitDialog` 以初始化對話方塊的控制項，例如設定編輯方塊的初始文字。 您必須從您的 `OnInitDialog` 覆寫呼叫基底類別 `CDialog` 的 `OnInitDialog` 成員函式。

如果您想要設定對話方塊的背景色彩（以及應用程式中的所有其他對話方塊），請參閱[設定對話方塊的背景色彩](setting-the-dialog-boxs-background-color.md)。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)
