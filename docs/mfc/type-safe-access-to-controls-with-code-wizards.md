---
title: 使用程式碼精靈的控制項類型安全存取
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: b49c1b6f21dfe5270e40649241812320303ad411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370908"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>使用程式碼精靈的控制項類型安全存取

如果您熟悉 DDX 功能,則可以使用[「添加成員變數精靈](../ide/add-member-variable-wizard.md)」中的「控制件」屬性創建類型安全訪問。 此方法比在沒有代碼嚮導的情況下創建控制項更容易。

如果只想訪問控制項的值,DDX會提供該值。 如果要執行更多操作,請使用「添加成員變數嚮導」將相應類的成員變數添加到對話框類中。 將此成員變數附加到 Control 屬性。

成員變數可以具有 Control 屬性而不是 Value 屬性。 Value 屬性引用從控制檔傳回的資料`CString`類型,例如或**int**。Control 屬性允許透過資料類型是 MFC 中的控制類之`CButton`一`CEdit`(如或) 的資料成員直接存取控制項。

> [!NOTE]
> 對於給定控制件,如果需要,可以具有具有 Value 屬性的多個成員變數,並且最多具有 Control 屬性的一個成員變數。 只能將一個 MFC 物件映射到控制項,因為連接到控制項或任何其他視窗的多個物件將導致消息映射中的歧義。

可以使用此物件調用控制項物件的任何成員函數。 此類調用會影響對話方塊中的控制項。 例如,對於由變數*m_Checkbox*表示的複選框控件`CButton`,可以調用:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

在這裡,成員變數*m_Checkbox*的作用與`GetMyCheckbox`[類型安全訪問無代碼嚮導中的控制項](../mfc/type-safe-access-to-controls-without-code-wizards.md)中顯示的成員函數相同。 如果複選框不是自動複選框,則按下該按鈕時,仍需要BN_CLICKED控制通知消息的對話方塊類中的處理程式。

有關控制項的詳細資訊,請參考[控制件](../mfc/controls-mfc.md)。

## <a name="see-also"></a>另請參閱

[對話方塊中之控制項的型別安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[不使用程式碼精靈的控制項類型安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)
