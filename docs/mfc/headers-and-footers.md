---
title: "頁首和頁尾 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7525cba7d05c4d04f0548bd2dc774503b284c220
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="headers-and-footers"></a>頁首和頁尾
本文說明如何將頁首和頁尾加入至列印的文件。  
  
 當您在螢幕上看到文件，文件名稱和文件中目前的位置通常會顯示在標題列和狀態列。 當檢視文件的列印複本時，在頁首或頁尾顯示名稱和頁碼會很有用。 即使 WYSIWYG 程式執行列印和螢幕顯示的方式有所不同，這個方法也通用。  
  
 [OnPrint](../mfc/reference/cview-class.md#onprint)成員函式是列印頁首或頁尾，因為它針對每個頁面，來呼叫，而且呼叫只適用於列印，不用於螢幕顯示的適當位置。 您可以定義不同的函式列印頁首或頁尾，並從 `OnPrint` 傳給它印表機裝置內容。 您可能需要調整視窗原點或範圍，然後再呼叫[OnDraw](../mfc/reference/cview-class.md#ondraw)避免頁面重疊頁首或頁尾的主體。 您可能也需要修改 `OnDraw`，因為頁面容納的文件數量會降低。  
  
 其中一種方式來補償頁首或頁尾所採取的區域是使用**m_rectDraw**隸屬[CPrintInfo](../mfc/reference/cprintinfo-structure.md)。 每次列印頁面，這個成員都會以頁面的可用區域初始化。 如果您要列印頁首或頁尾列印頁面主體前，您可以減少儲存在矩形的大小**m_rectDraw**至頁首或頁尾所採取的區域。 然後`OnPrint`可以參考**m_rectDraw**找出列印頁面主體會保留多少區域。  
  
 您無法列印標頭，或任何其他項目， [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)，因為它之前，會呼叫`StartPage`成員函式[CDC](../mfc/reference/cdc-class.md)已呼叫。 此時，印表機裝置內容視為在分頁界限。 您只可以從 `OnPrint` 成員函式執行列印。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [列印多頁文件](../mfc/multipage-documents.md)  
  
-   [列印配置 GDI 資源](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>請參閱  
 [列印](../mfc/printing.md)

