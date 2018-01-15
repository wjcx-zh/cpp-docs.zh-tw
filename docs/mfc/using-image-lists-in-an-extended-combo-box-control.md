---
title: "擴充的下拉式方塊控制項中使用影像清單 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ac69e7d0dbe1748a409b107579c747b7f9a4a7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>在擴充的下拉式方塊控制項中使用影像清單
擴充的下拉式方塊控制項的主要功能是能夠將映像從影像清單與下拉式方塊控制項中的個別項目產生關聯。 每個項目是可以顯示三個不同的映像： 一個為其選取的狀態，另一個適用於其未選取的狀態，以及協力廠商的覆疊影像。  
  
 下列程序會將影像清單與擴充的下拉式方塊控制項產生關聯：  
  
### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>影像清單與擴充的下拉式方塊控制項  
  
1.  建構新的影像清單 （或使用現有的影像清單物件），使用[CImageList](../mfc/reference/cimagelist-class.md)建構函式，並儲存結果的指標。  
  
2.  初始化新的影像清單物件藉由呼叫[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下列程式碼是此呼叫的範例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  新增選用的映像的每個可能狀態： 選取或未選取，以及重疊。 下列程式碼會加入三個預先定義的映像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  關聯的影像清單與呼叫控制項[CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist)。  
  
 一旦已與控制項關聯的影像清單，您可以個別指定每個項目會使用三種可能狀態的映像。 如需詳細資訊，請參閱[設定個別項目的影像](../mfc/setting-the-images-for-an-individual-item.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控制項](../mfc/controls-mfc.md)

