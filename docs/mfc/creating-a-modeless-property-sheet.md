---
title: 建立非強制回應屬性工作表
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 90f6dcd5659d308a4b39d6a7d5a42003fc1f2111
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685687"
---
# <a name="creating-a-modeless-property-sheet"></a>建立非強制回應屬性工作表

一般來說，您建立的屬性工作表將會是強制回應。 使用強制回應屬性工作表時，使用者必須先關閉屬性工作表，才能使用應用程式的任何其他部分。 本文描述您可以用來建立非模式屬性工作表的方法，讓使用者可以在使用應用程式的其他部分時，讓屬性工作表保持開啟。

若要將屬性工作表顯示為非強制回應對話方塊，而不是強制回應對話方塊，請呼叫[CPropertySheet：： Create](../mfc/reference/cpropertysheet-class.md#create) ，而不要使用[DoModal](../mfc/reference/cpropertysheet-class.md#domodal)。 您也必須執行一些額外的工作，以支援非模式屬性工作表。

其中一項額外的工作，就是在屬性工作表和內容工作表開啟時，在屬性工作表和其正在修改的外部物件之間交換資料。 這通常與標準非強制回應對話方塊的工作相同。 這項工作的一部分，是在非強制回應屬性工作表與屬性設定所套用的外部物件之間，進行通訊的通道。 如果您從[CPropertySheet](../mfc/reference/cpropertysheet-class.md)為非強制回應屬性工作表衍生一個類別，這個實做會變得更容易。 本文假設您已完成這項作業。

無模式屬性工作表和外部物件之間通訊的一種方法（例如，在視圖中的目前選取範圍）是定義從屬性工作表到外部物件的指標。 定義 `CPropertySheet`衍生類別中的函式（稱為 `SetMyExternalObject`），以在焦點從某個外部物件變更為另一個時變更指標。 `SetMyExternalObject` 函數需要重設每個屬性頁的設定，以反映新選取的外部物件。 若要完成此工作，`SetMyExternalObject` 函式必須能夠存取屬於 `CPropertySheet` 類別的[CPropertyPage](../mfc/reference/cpropertypage-class.md)物件。

在屬性工作表中提供屬性頁存取最方便的方式，就是將 `CPropertyPage` 物件內嵌在 `CPropertySheet`衍生的物件中。 在 `CPropertySheet`衍生物件中內嵌 `CPropertyPage` 物件與強制回應對話方塊的一般設計不同，其中屬性工作表的擁有者會建立 `CPropertyPage` 物件，並透過[CPropertySheet：： AddPage](../mfc/reference/cpropertysheet-class.md#addpage)將它們傳遞至屬性工作表。

有許多使用者介面的替代方案，可用於判斷非強制回應屬性工作表的設定何時應套用至外部物件。 另一個替代方式是在使用者變更任何值時，套用目前屬性頁的設定。 另一個替代方式是提供 [套用] 按鈕，讓使用者可以在將屬性頁中的變更認可到外部物件之前，先累積這些變更。 如需處理 [套用] 按鈕方式的相關資訊，請參閱[處理套用按鈕](../mfc/handling-the-apply-button.md)的文章。

## <a name="see-also"></a>另請參閱

[屬性工作表](../mfc/property-sheets-mfc.md)<br/>
[交換資料](../mfc/exchanging-data.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)
