---
title: Rich Edit 控制項中的斷字法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f012897d968d108cb366126fc38992ff1dd11d0a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424608"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Rich Edit 控制項中的斷字法

Rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 呼叫函式稱為 「 文字中斷程序 「 若要尋找文字之間的中斷，並判斷它可以在此中斷行。 在執行自動換行作業，以及在處理 CTRL+LEFT 和 CTRL+RIGHT 的組合鍵時，控制項會使用這個資訊。 應用程式可以傳送訊息至 Rich Edit 控制項來取代預設斷字程序、擷取斷字資訊，以及決定指定的字元落在哪一行的位置。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

