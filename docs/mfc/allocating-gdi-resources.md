---
title: 配置 GDI 資源
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: adfd8b19f683b82eec213890c8e1345e070ff3ec
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504622"
---
# <a name="allocating-gdi-resources"></a>配置 GDI 資源

本文說明如何配置和取消配置列印所需的 Windows 圖形裝置介面 (GDI) 物件。

> [!NOTE]
>  如需詳細資訊，請參閱 < [GDI + SDK 文件](/windows/desktop/gdiplus/-gdiplus-gdi-start)。

假設您需要使用特定字型、畫筆或其他 GDI 物件進行列印，但不用於螢幕顯示。 在應用程式啟動時配置這些物件需要較多記憶體，因此不符合效益。 當應用程式未列印文件時，這些記憶體可能需要用於其他用途。 在列印開始時配置這些物件，然後在列印結束時加以刪除，是較理想的做法。

若要配置這些 GDI 物件，覆寫[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)成員函式。 此函式是很適合此用途的原因有二： 架構會呼叫此函式一次在每個列印工作，而且不同於開頭[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)，此函式具有存取權[CDC](../mfc/reference/cdc-class.md)物件，代表印表機裝置驅動程式。 您可以列印工作儲存使用這些物件，藉由定義指向 GDI 物件的檢視類別中的成員變數 (例如`CFont *`成員等等)。

若要使用您所建立的 GDI 物件，將其選取至印表機裝置內容中[OnPrint](../mfc/reference/cview-class.md#onprint)成員函式。 如果您需要不同的 GDI 物件的文件的不同頁面時，您可以檢查`m_nCurPage`隸屬[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構，並據以選取 GDI 物件。 如果您的數個連續頁面需要某個 GDI 物件，Windows 會要求您在每次呼叫 `OnPrint` 時將其選取至裝置內容中。

若要取消配置這些 GDI 物件，覆寫[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)成員函式。 架構會每個列印工作結束時呼叫此函式，讓您有機會在應用程式回到其他工作之前取消配置列印特定 GDI 物件。

## <a name="see-also"></a>另請參閱

[列印](../mfc/printing.md)<br/>
[如何完成預設列印](../mfc/how-default-printing-is-done.md)
