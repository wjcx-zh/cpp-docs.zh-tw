---
title: 設定個別項目的影像
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 177c06acfe665a43921b19407d9d357d4545e748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511283"
---
# <a name="setting-the-images-for-an-individual-item"></a>設定個別項目的影像

擴充的下拉式列示方塊專案所使用的不同影像類型, 取決於[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)結構的*iImage*、 *iSelectedImage*和*iOverlay*成員中的值。 每個值都是控制項之關聯影像清單中的影像索引。 根據預設, 這些成員會設定為 0, 使控制項不會顯示專案的影像。 如果您想要使用特定專案的影像, 您可以在插入下拉式方塊專案或修改現有的下拉式方塊專案時, 據以修改結構。

## <a name="setting-the-image-for-a-new-item"></a>設定新專案的影像

如果您要插入新的專案, 請使用適當的值來初始化*iImage*、 *iSelectedImage*和*iOverlay*結構成員, 然後使用[CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem)的呼叫來插入專案。

下列範例會將新的擴充下拉式方塊專案 (`cbi`) 插入擴充的下拉式方塊控制項 (`m_comboEx`), 並提供所有三個影像狀態的索引:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>設定現有專案的影像

如果您要修改現有的專案, 就必須使用**COMBOBOXEXITEM**結構的*mask*成員。

#### <a name="to-modify-an-existing-item-to-use-images"></a>若要修改現有的專案以使用影像

1. 宣告**COMBOBOXEXITEM**結構, 並將*mask*資料成員設為您想要修改的值。

1. 使用這個結構, 對[CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem)進行呼叫。

1. 使用適當的值, 修改新傳回結構的*mask*、 *iImage*和*iSelectedImage*成員。

1. 呼叫[CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem), 傳入已修改的結構。

下列範例會藉由交換第三個擴充下拉式方塊專案的已選取和未選取影像, 來示範此程式:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控制項](../mfc/controls-mfc.md)
