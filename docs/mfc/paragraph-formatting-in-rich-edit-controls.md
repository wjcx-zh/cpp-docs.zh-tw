---
title: Rich Edit 控制項中的段落格式化
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: 0988e7940c8d8947b86e97a35d71586f8f5c316a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916379"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Rich Edit 控制項中的段落格式化

您可以使用 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 的成員函式來格式化段落, 並取得格式資訊。 段落格式屬性包含對齊、定位點、縮排和編號。

您可以使用[SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat)成員函式套用段落格式。 若要判斷所選取文字的目前段落格式, 請使用[GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat)成員函式。 [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-paraformat)結構會與這些成員函式搭配使用, 以指定段落屬性。 **PARAFORMAT**的其中一個重要成員是*dwMask*。 在`SetParaFormat`中, *dwMask*會指定要由這個函式呼叫設定的段落屬性。 `GetParaFormat`報告選取範圍中第一個段落的屬性;*dwMask*會指定在整個選取範圍中一致的屬性。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
