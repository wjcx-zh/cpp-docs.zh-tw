---
title: 設定個別項目的影像 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aec02a07de8fad2f9ad063295090be5ace4146e6
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953798"
---
# <a name="setting-the-images-for-an-individual-item"></a>設定個別項目的影像
擴充的下拉式方塊項目所使用的影像的不同類型取決於中的值*iImage*， *iSelectedImage*，和*iOverlay* 的成員[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)結構。 每個值是控制項的相關聯的影像清單中的映像的索引。 根據預設，這些成員會設定為 0，使控制項來不顯示項目的任何影像。 如果您想要使用特定的項目以映像，您可以修改結構同理，當插入下拉式方塊項目或是藉由修改現有的下拉式方塊項目。  
  
## <a name="setting-the-image-for-a-new-item"></a>新的項目設定映像  
 如果您要插入新項目，初始化*iImage*， *iSelectedImage*，和*iOverlay*結構成員，以適當的值，然後再插入的項目，藉由呼叫[CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem)。  
  
 下列範例會將新的擴充的下拉式方塊項目 (`cbi`) 成擴充的下拉式方塊控制項 (`m_comboEx`)，全部三個影像的影像狀態提供索引：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>設定現有項目的影像  
 如果您要修改現有的項目，您需要使用*遮罩*隸屬**COMBOBOXEXITEM**結構。  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>若要修改現有的項目以使用影像  
  
1.  宣告**COMBOBOXEXITEM**結構，並設定*遮罩*您感興趣修改資料成員的值。  
  
2.  使用此結構中，呼叫以[CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem)。  
  
3.  修改*遮罩*， *iImage*，和*iSelectedImage*成員的新傳回的結構，使用適當的值。  
  
4.  呼叫以[CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem)，並傳入修改過的結構。  
  
 下列範例會示範此程序，藉由交換的選取和取消選取映像的第三個擴充的下拉式方塊項目：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控制項](../mfc/controls-mfc.md)

