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
ms.openlocfilehash: 04bf49371b3ab5eaaad2775b532d8d35bf990ce3
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915283"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Rich Edit 控制項中的資料流作業

您可以使用資料流程, 將資料傳入或傳出 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 資料流程是由[EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-editstream)結構所定義, 它會指定緩衝區和應用程式定義的回呼函式。

若要將資料讀入 rich edit 控制項 (也就是將中的資料串流), 請使用[StreamIn](../mfc/reference/cricheditctrl-class.md#streamin)成員函式。 控制項會重複呼叫應用程式定義的回呼函式，每一次呼叫都會將一部分的資料傳送至緩衝區。

若要儲存 rich edit 控制項的內容 (也就是將資料串流), 您可以使用[StreamOut](../mfc/reference/cricheditctrl-class.md#streamout)成員函式。 此控制項會將資料重複寫入緩衝區，然後再呼叫應用程式定義的回呼函式。 回呼函式會在每次呼叫時儲存緩衝區的內容。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
