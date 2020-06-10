---
title: 配置 GDI 資源
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: f0cadac5320a8c6e91eb3b1989d1fb3c0c701eb0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623240"
---
# <a name="allocating-gdi-resources"></a>配置 GDI 資源

本文說明如何配置和取消配置列印所需的 Windows 圖形裝置介面 (GDI) 物件。

> [!NOTE]
> 如需詳細資訊，請參閱[Gdi + SDK 檔](/windows/win32/gdiplus/-gdiplus-gdi-start)。

假設您需要使用特定字型、畫筆或其他 GDI 物件進行列印，但不用於螢幕顯示。 在應用程式啟動時配置這些物件需要較多記憶體，因此不符合效益。 當應用程式未列印文件時，這些記憶體可能需要用於其他用途。 在列印開始時配置這些物件，然後在列印結束時加以刪除，是較理想的做法。

若要配置這些 GDI 物件，請覆寫[OnBeginPrinting](reference/cview-class.md#onbeginprinting)成員函式。 此函式很適合此用途，原因有兩個：架構會在每個列印工作開始時呼叫此函式一次，而且與[OnPreparePrinting](reference/cview-class.md#onprepareprinting)不同，此函式可存取代表印表機設備磁碟機的[CDC](reference/cdc-class.md)物件。 您可以儲存這些物件，以便在列印工作期間使用，方法是在 view 類別中定義指向 GDI 物件（例如，成員等等）的成員變數 `CFont *` 。

若要使用您所建立的 GDI 物件，請在 [ [OnPrint](reference/cview-class.md#onprint) ] 成員函式的印表機裝置內容中選取它們。 如果檔的不同頁面需要不同的 GDI 物件，您可以檢查 `m_nCurPage` [CPrintInfo](reference/cprintinfo-structure.md)結構的成員，並據以選取 gdi 物件。 如果您的數個連續頁面需要某個 GDI 物件，Windows 會要求您在每次呼叫 `OnPrint` 時將其選取至裝置內容中。

若要解除配置這些 GDI 物件，請覆寫[OnEndPrinting](reference/cview-class.md#onendprinting)成員函式。 架構會每個列印工作結束時呼叫此函式，讓您有機會在應用程式回到其他工作之前取消配置列印特定 GDI 物件。

## <a name="see-also"></a>另請參閱

[列印](printing.md)<br/>
[如何完成預設列印](how-default-printing-is-done.md)
