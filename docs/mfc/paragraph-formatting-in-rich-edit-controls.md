---
title: Rich Edit 控制項中的段落格式化
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: f79d9a97554e2f73b42746c9e9094b07a37513d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581970"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Rich Edit 控制項中的段落格式化

您可以使用 rich edit 控制項的成員函式 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 來格式化段落和擷取格式化資訊。 段落格式屬性包含對齊、定位點、縮排和編號。

您可以套用格式化所使用的段落[SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat)成員函式。 若要判斷目前的段落格式選取的文字，請使用[GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat)成員函式。 [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-_paraformat)結構搭配這些成員函式以指定段落屬性。 其中一個重要成員**PARAFORMAT**是*dwMask*。 在  `SetParaFormat`， *dwMask*指定那些段落屬性會設定由這個函式呼叫。 `GetParaFormat` 報告選取範圍; 中的第一個段落的屬性*dwMask*指定之屬性的選取範圍中一致。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

