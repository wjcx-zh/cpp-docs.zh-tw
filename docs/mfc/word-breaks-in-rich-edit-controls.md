---
title: Rich Edit 控制項中的斷字法
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: e71643350ced5b8ecff7c8ac7829741cc3e8493b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399534"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Rich Edit 控制項中的斷字法

Rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 呼叫函式稱為 「 文字中斷程序 「 若要尋找文字之間的中斷，並判斷它可以在此中斷行。 在執行自動換行作業，以及在處理 CTRL+LEFT 和 CTRL+RIGHT 的組合鍵時，控制項會使用這個資訊。 應用程式可以傳送訊息至 Rich Edit 控制項來取代預設斷字程序、擷取斷字資訊，以及決定指定的字元落在哪一行的位置。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
