---
title: 在擴充的下拉式方塊控制項中使用影像清單
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 6e4d983d53e49fc8d9c80c206f1a23078eb82f61
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266987"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>在擴充的下拉式方塊控制項中使用影像清單

擴充的下拉式方塊控制項的主要功能是能夠從影像清單的映像相關聯的下拉式方塊控制項中的個別項目。 每個項目可顯示三個不同的映像： 一個用於其選取的狀態，另一個用於其選定的狀態，而第三個重疊影像。

下列程序會將影像清單與擴充的下拉式方塊控制項產生關聯：

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>擴充的下拉式方塊控制項相關聯的映像清單

1. 建構新的影像清單 （或使用現有的影像清單物件），使用[CImageList](../mfc/reference/cimagelist-class.md)建構函式，並儲存結果的指標。

1. 藉由呼叫初始化新的影像清單物件[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下列程式碼是此呼叫的其中一個範例。

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. 新增選擇性的映像的每個可能狀態： 選取或未選取，以及重疊。 下列程式碼會新增三個預先定義的映像。

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. 影像清單關聯的控制項，藉由呼叫[CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist)。

一旦影像清單與控制項相關聯，您可以個別指定每個項目將會使用三種可能狀態的映像。 如需詳細資訊，請參閱 <<c0> [ 設定個別項目的影像](../mfc/setting-the-images-for-an-individual-item.md)。

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控制項](../mfc/controls-mfc.md)
