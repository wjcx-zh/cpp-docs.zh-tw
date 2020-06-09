---
title: 頁首和頁尾
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
ms.openlocfilehash: 7024c57dbe41a579582d409d0536db0ca0bc46d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620101"
---
# <a name="headers-and-footers"></a>頁首和頁尾

本文說明如何將頁首和頁尾加入至列印的文件。

當您在螢幕上看到文件，文件名稱和文件中目前的位置通常會顯示在標題列和狀態列。 當檢視文件的列印複本時，在頁首或頁尾顯示名稱和頁碼會很有用。 即使 WYSIWYG 程式執行列印和螢幕顯示的方式有所不同，這個方法也通用。

[OnPrint](reference/cview-class.md#onprint)成員函式是列印頁首或頁尾的適當位置，因為它是針對每個頁面呼叫，而且只會針對列印呼叫，而不是針對螢幕顯示。 您可以定義不同的函式列印頁首或頁尾，並從 `OnPrint` 傳給它印表機裝置內容。 在呼叫[OnDraw](reference/cview-class.md#ondraw)之前，您可能需要調整視窗原點或範圍，以避免頁面的主體與頁首或頁尾重迭。 您可能也需要修改 `OnDraw`，因為頁面容納的文件數量會降低。

補償頁首或頁尾所取得之區域的其中一種方式是使用[CPrintInfo](reference/cprintinfo-structure.md)的**m_rectDraw**成員。 每次列印頁面，這個成員都會以頁面的可用區域初始化。 如果您在列印頁面的主體之前列印頁首或頁尾，您可以減少儲存在**m_rectDraw**中的矩形大小，以考慮頁首或頁尾所拍攝的區域。 然後 `OnPrint` 可以參考**m_rectDraw** ，找出列印頁面主體所需的區域數量。

您無法從[OnPrepareDC](reference/cview-class.md#onpreparedc)列印標頭或其他任何專案，因為它是在 `StartPage` 呼叫[CDC](reference/cdc-class.md)的成員函式之前呼叫。 此時，印表機裝置內容視為在分頁界限。 您只可以從 `OnPrint` 成員函式執行列印。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [列印多頁檔](multipage-documents.md)

- [配置列印的 GDI 資源](allocating-gdi-resources.md)

## <a name="see-also"></a>另請參閱

[列印](printing.md)
