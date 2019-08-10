---
title: Rich Edit 控制項中的列印
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 6ae7212eaa8eed1088a507973c80311f169c7751
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916272"
---
# <a name="printing-in-rich-edit-controls"></a>Rich Edit 控制項中的列印

您可以告訴 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), 針對指定的裝置 (例如印表機) 呈現其輸出。 您也可以指定輸出裝置, 讓 rich edit 控制項將其文字格式化。

若要為特定裝置格式化 rich edit 控制項的部分內容, 您可以使用[FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange)成員函式。 搭配此函式使用的[FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-formatrange)結構會指定要格式化的文字範圍, 以及目標裝置的裝置內容 (DC)。

格式化輸出裝置的文字之後, 您可以使用[DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband)成員函式將輸出傳送至裝置。 藉由重複`FormatRange`使用`DisplayBand`和, 列印豐富編輯控制項內容的應用程式可以執行分級。 (等量會將輸出分割成較小的部分, 以供列印之用)。

您可以使用[SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice)成員函式來指定 [rich edit] 控制項將其文字格式化的目標裝置。 此函式適用于 WYSIWYG (您所看到的內容) 格式, 其中應用程式會使用預設印表機的字型度量 (而非螢幕) 來放置文字。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
