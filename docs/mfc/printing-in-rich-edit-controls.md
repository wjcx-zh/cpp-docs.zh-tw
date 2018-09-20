---
title: Rich Edit 控制項中的列印 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38389f62ebeeaccf6b7b4c211b056b6f6c3ac188
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421319"
---
# <a name="printing-in-rich-edit-controls"></a>Rich Edit 控制項中的列印

您所見的 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 來呈現其輸出指定的裝置，例如印表機。 您也可以指定的 rich edit 控制項的輸出裝置格式化文字。

若要格式化的特定裝置的 rich edit 控制項內容的一部分，您可以使用[FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange)成員函式。 [FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-_formatrange)結構搭配此函式使用指定的目標裝置的裝置內容 (DC) 以及格式化的文字範圍。

格式化文字的輸出裝置之後, 您可以將輸出傳送給裝置使用[DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband)成員函式。 藉由重複`FormatRange`和`DisplayBand`，列印出 rich edit 控制項內容的應用程式可以實作矩形。 （矩形會分成較小部分的輸出以便列印）。

您可以使用[SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice)來指定目標裝置的 rich edit 控制項的成員函式會將其文字的格式化。 此函式可用於使用 WYSIWYG （所見即所得） 格式，在其中應用程式將使用預設印表機的字型度量資訊，而不螢幕的文字。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

