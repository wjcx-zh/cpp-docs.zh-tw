---
title: Rich Edit 控制項中的資料流作業
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 099b29a3a3ff1337c71d14d1ae7bfa0a182a6903
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584402"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Rich Edit 控制項中的資料流作業

您可以使用資料流將資料送入或送出 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 所定義的資料流[EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-_editstream)結構，指定緩衝區和應用程式定義的回呼函式。

若要讀取資料讀入 rich edit 控制項 （也就是資料流中的資料）、 使用[StreamIn](../mfc/reference/cricheditctrl-class.md#streamin)成員函式。 控制項會重複呼叫應用程式定義的回呼函式，每一次呼叫都會將一部分的資料傳送至緩衝區。

若要儲存內容豐富的編輯控制項 （也就是串流處理資料輸出），您可以使用[StreamOut](../mfc/reference/cricheditctrl-class.md#streamout)成員函式。 此控制項會將資料重複寫入緩衝區，然後再呼叫應用程式定義的回呼函式。 回呼函式會在每次呼叫時儲存緩衝區的內容。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

