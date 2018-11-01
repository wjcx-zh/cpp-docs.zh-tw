---
title: 設定個別項目的影像
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 61e152534dbea09fbca0af819b0847e82a1c4146
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512069"
---
# <a name="setting-the-images-for-an-individual-item"></a>設定個別項目的影像

擴充的下拉式方塊項目所使用的映像不同的類型取決於中的值*iImage*， *iSelectedImage*，並*iOverlay* 的成員[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)結構。 每個值是控制項相關聯的映像清單中的映像的索引。 根據預設，這些成員會設定為 0，使控制項來不顯示項目的任何影像。 如果您想要用於特定的項目中的映像，您可以修改結構因此，當插入下拉式方塊項目或修改現有的下拉式方塊項目。

## <a name="setting-the-image-for-a-new-item"></a>新的項目設定的映像

如果您要插入新項目，初始化*iImage*， *iSelectedImage*，並*iOverlay*結構成員，以適當的值，然後再插入的項目，藉由呼叫[CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem)。

下列範例會插入新的擴充的下拉式方塊項目 (`cbi`) 到擴充的下拉式方塊控制項 (`m_comboEx`)，提供索引的所有三個映像狀態：

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>現有的項目設定的映像

如果您要修改現有的項目，您需要使用*遮罩*隸屬**COMBOBOXEXITEM**結構。

#### <a name="to-modify-an-existing-item-to-use-images"></a>若要修改現有的項目使用映像

1. 宣告**COMBOBOXEXITEM**結構，並設定*遮罩*您感興趣修改資料成員的值。

1. 使用此結構中，請呼叫[CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem)。

1. 修改*遮罩*， *iImage*，並*iSelectedImage*成員的新傳回的結構中，使用適當的值。

1. 呼叫以[CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem)，並傳入修改過的結構。

下列範例會示範此程序，藉由交換的選取和取消選取映像的第三個擴充的下拉式方塊項目：

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控制項](../mfc/controls-mfc.md)

