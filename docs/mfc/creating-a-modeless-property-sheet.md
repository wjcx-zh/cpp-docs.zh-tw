---
title: 建立非強制回應屬性工作表 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10dbef813d922bd01a5f9215b6d6e642349d2b75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-modeless-property-sheet"></a>建立非強制回應屬性工作表
一般來說，您建立屬性工作表為強制回應。 當使用強制回應屬性工作表時，使用者必須先關閉屬性工作表之前使用的應用程式的任何其他部分。 本文描述您可用來建立可讓使用者使用應用程式的其他部分時，將屬性工作表保持開啟的非強制回應屬性工作表的方法。  
  
 若要顯示屬性工作表為非強制回應對話方塊而不是為強制回應對話方塊，請呼叫[CPropertySheet::Create](../mfc/reference/cpropertysheet-class.md#create)而不是[DoModal](../mfc/reference/cpropertysheet-class.md#domodal)。 您也必須實作一些額外的工作，以支援非強制回應屬性工作表。  
  
 其中一項額外的工作交換屬性工作表和屬性工作表開啟時，它正在修改的外部物件之間的資料。 這通常是相同的工作與標準的非強制回應對話方塊。 此工作的一部分實作外部物件的屬性設定適用於非強制回應屬性工作表之間的通訊的通道。 這個實作是很不容易，如果您是衍生自[CPropertySheet](../mfc/reference/cpropertysheet-class.md)程式非強制回應屬性工作表。 本文假設您這樣做。  
  
 非強制回應屬性工作表和外部之間通訊的一種方法是定義外部物件的指標從屬性工作表物件 （在檢視中，例如目前選取範圍）。 定義函式 (稱為類似`SetMyExternalObject`) 中`CPropertySheet`-衍生的類別，將指標變更當焦點從某個外部物件變更到另一個。 `SetMyExternalObject`函式需要重設的每個屬性頁設定，以反映新選取的外部物件。 若要達成此目的，`SetMyExternalObject`函式必須要能夠存取[CPropertyPage](../mfc/reference/cpropertypage-class.md)屬於物件`CPropertySheet`類別。  
  
 提供存取權的屬性工作表內的屬性頁最方便的方式是將內嵌`CPropertyPage`中的物件`CPropertySheet`-衍生物件。 內嵌`CPropertyPage`中的物件`CPropertySheet`-衍生的物件不同於強制回應對話方塊，其中會建立屬性工作表的擁有者的一般設計`CPropertyPage`物件，並將其傳遞至屬性工作表，以透過[Cpropertysheet:: Addpage](../mfc/reference/cpropertysheet-class.md#addpage)。  
  
 有許多使用者介面替代方案，以判斷當非強制回應屬性工作表設定應該套用至外部物件。 一種替代方法是套用目前屬性頁的設定，每當使用者變更任何值。 另一個替代方式是提供 [套用] 按鈕，可讓使用者累積之前認可這些外部物件的屬性頁中的變更。 方式處理 [套用] 按鈕上的資訊，請參閱文章[處理套用按鈕](../mfc/handling-the-apply-button.md)。  
  
## <a name="see-also"></a>另請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)   
 [交換資料](../mfc/exchanging-data.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

