---
title: Rich Edit 控制項中的列印
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: f275078fbef9026363305bb714da3a2af333c91f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619813"
---
# <a name="printing-in-rich-edit-controls"></a>Rich Edit 控制項中的列印

您可以告訴 rich edit 控制項（[CRichEditCtrl](reference/cricheditctrl-class.md)），針對指定的裝置（例如印表機）呈現其輸出。 您也可以指定輸出裝置，讓 rich edit 控制項將其文字格式化。

若要為特定裝置格式化 rich edit 控制項的部分內容，您可以使用[FormatRange](reference/cricheditctrl-class.md#formatrange)成員函式。 搭配此函式使用的[FORMATRANGE](/windows/win32/api/richedit/ns-richedit-formatrange)結構會指定要格式化的文字範圍，以及目標裝置的裝置內容（DC）。

格式化輸出裝置的文字之後，您可以使用[DisplayBand](reference/cricheditctrl-class.md#displayband)成員函式將輸出傳送至裝置。 藉由重複使用 `FormatRange` 和 `DisplayBand` ，列印豐富編輯控制項內容的應用程式可以執行分級。 （等量會將輸出分割成較小的部分，以供列印之用）。

您可以使用[SetTargetDevice](reference/cricheditctrl-class.md#settargetdevice)成員函式來指定 [rich edit] 控制項將其文字格式化的目標裝置。 此函式適用于 WYSIWYG （您所看到的內容）格式，其中應用程式會使用預設印表機的字型度量（而非螢幕）來放置文字。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控制項](controls-mfc.md)
