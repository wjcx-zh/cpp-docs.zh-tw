---
title: 列印
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 3d2ef494be66171cbcbf2b8b9e19c29c8bdc5c2f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619808"
---
# <a name="printing"></a>列印

Microsoft Windows 會執行與裝置無關的顯示。 在 MFC 中，這表示在您 view 類別的成員函式中，相同的繪圖呼叫 `OnDraw` 會負責在顯示器上和其他裝置（例如印表機）上進行繪製。 針對 [預覽列印]，目標裝置是顯示的模擬印表機輸出。

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>您在列印中的角色與架構的角色

您的 view 類別具有下列責任：

- 通知架構檔中有多少頁面。

- 當系統要求您列印指定的頁面時，請繪製該部分的檔。

- 配置和解除配置列印所需的任何字型或其他圖形裝置介面（GDI）資源。

- 如有必要，請在列印特定頁面之前，傳送變更印表機模式所需的任何換用程式碼，例如，變更每頁的列印方向。

架構的職責如下所示：

- 顯示 [**列印**] 對話方塊。

- 建立印表機的[CDC](reference/cdc-class.md)物件。

- 呼叫物件的[StartDoc](reference/cdc-class.md#startdoc)和[EndDoc](reference/cdc-class.md#enddoc)成員函式 `CDC` 。

- 重複呼叫物件的[StartPage](reference/cdc-class.md#startpage)成員函式 `CDC` ，通知 view 類別應該列印哪一個頁面，並呼叫物件的[EndPage](reference/cdc-class.md#endpage)成員函式 `CDC` 。

- 在適當的時間呼叫視圖中的可覆寫函式。

下列文章討論架構如何支援列印和預覽列印：

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [如何完成預設列印](how-default-printing-is-done.md)

- [多頁檔](multipage-documents.md)

- [頁首和頁尾](headers-and-footers.md)

- [配置列印的 GDI 資源](allocating-gdi-resources.md)

- [預覽列印](print-preview-architecture.md)

## <a name="see-also"></a>另請參閱

[列印和預覽列印](printing-and-print-preview.md)
