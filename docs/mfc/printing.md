---
title: 列印
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: a46096592c9983d04d2122bfabb56ece9346c4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371197"
---
# <a name="printing"></a>列印

微軟視窗實現與設備無關的顯示。 在 MFC 中,這意味著檢視`OnDraw`類的成員函數中的相同繪圖調用負責在顯示器和其他設備(如印表機)上進行繪圖。 對於列印預覽,目標設備是列印到顯示器的類比印表機輸出。

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>您在列印中的角色與框架的角色

您的檢視類具有以下職責:

- 通知框架文件中有多少頁。

- 當要求列印指定的頁面時,繪製文檔的該部分。

- 分配和取消分配列印所需的任何字體或其他圖形設備介面 (GDI) 資源。

- 如有必要,在列印給定頁面之前發送更改印表機模式所需的任何轉義代碼,例如,以每頁更改列印方向。

該框架的職責如下:

- 顯示 **「列印」** 對話方塊。

- 為印表機創建[CDC](../mfc/reference/cdc-class.md)物件。

- 呼叫`CDC`物件的[StartDoc](../mfc/reference/cdc-class.md#startdoc)和[EndDoc](../mfc/reference/cdc-class.md#enddoc)成員函數。

- `CDC`重複調用物件的[StartPage](../mfc/reference/cdc-class.md#startpage)成員函數,通知應列印哪個頁面的檢視類,並調`CDC`用 物件的[EndPage](../mfc/reference/cdc-class.md#endpage)成員函數。

- 在適當的時間調用檢視中的可重寫函數。

以下文章討論框架如何支援列印和列印預覽:

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [如何執行預設列印](../mfc/how-default-printing-is-done.md)

- [多頁文件](../mfc/multipage-documents.md)

- [標題與註腳](../mfc/headers-and-footers.md)

- [配置列印的 GDI 資源](../mfc/allocating-gdi-resources.md)

- [預覽](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>另請參閱

[列印和預覽列印](../mfc/printing-and-print-preview.md)
