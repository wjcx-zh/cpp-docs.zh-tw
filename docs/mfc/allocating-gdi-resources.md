---
title: 配置 GDI 資源
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 149aefeade6f99c294b12bfb294cdf1addb9e5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370843"
---
# <a name="allocating-gdi-resources"></a>配置 GDI 資源

本文說明如何配置和取消配置列印所需的 Windows 圖形裝置介面 (GDI) 物件。

> [!NOTE]
> 有關詳細資訊,請參閱[GDI+ SDK 文件](/windows/win32/gdiplus/-gdiplus-gdi-start)。

假設您需要使用特定字型、畫筆或其他 GDI 物件進行列印，但不用於螢幕顯示。 在應用程式啟動時配置這些物件需要較多記憶體，因此不符合效益。 當應用程式未列印文件時，這些記憶體可能需要用於其他用途。 在列印開始時配置這些物件，然後在列印結束時加以刪除，是較理想的做法。

要分配這些 GDI 物件,可以重寫[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)成員函數。 此功能非常適合此目的,原因有二:框架在每個列印作業開始時調用此函數一次,與[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)不同,此功能可以訪問表示印表機裝置驅動程式的[CDC](../mfc/reference/cdc-class.md)物件。 通過在檢視類中定義指向 GDI 物件的成員變數(例如,`CFont *`成員等),可以儲存這些物件以便在列印作業期間使用。

要使用已創建的 GDI 物件,請在[OnPrint](../mfc/reference/cview-class.md#onprint)成員函數中選擇它們到印表機裝置上下文中。 如果文件的不同頁面需要不同的 GDI 物件,`m_nCurPage`可以檢查[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構的成員並相應地選擇 GDI 物件。 如果您的數個連續頁面需要某個 GDI 物件，Windows 會要求您在每次呼叫 `OnPrint` 時將其選取至裝置內容中。

要取消分配這些 GDI 物件,可以重寫[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)成員函數。 架構會每個列印工作結束時呼叫此函式，讓您有機會在應用程式回到其他工作之前取消配置列印特定 GDI 物件。

## <a name="see-also"></a>另請參閱

[列印](../mfc/printing.md)<br/>
[如何完成預設列印](../mfc/how-default-printing-is-done.md)
