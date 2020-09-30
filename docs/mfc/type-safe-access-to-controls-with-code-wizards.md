---
title: 使用程式碼精靈的控制項類型安全存取
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: ee7c49f75dcdc2b6c32f2b391ace7260b46d197b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507893"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>使用程式碼精靈的控制項類型安全存取

如果您熟悉 DDX 功能，您可以使用 [ [加入成員變數] Wizard](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) 中的 [控制項] 屬性來建立型別安全存取。 這種方法比在沒有程式碼嚮導的情況下建立控制項更容易。

如果您只想要存取控制項的值，則 DDX 會提供它。 如果您想要執行超過控制項值的存取權，請使用 [加入成員變數] Wizard，將適當類別的成員變數加入至對話方塊類別。 將這個成員變數附加到控制項屬性。

成員變數可以有控制項屬性，而不是 Value 屬性。 值屬性是指從控制項傳回的資料類型，例如 `CString` 或 **`int`** 。 控制項屬性可讓您透過類型為 MFC 中其中一個控制項類別的資料成員，直接存取控制項，例如 `CButton` 或 `CEdit` 。

> [!NOTE]
> 針對特定控制項，您可以視需要使用 [值] 屬性的多個成員變數，以及最多一個具有控制項屬性的成員變數。 您只能有一個 MFC 物件對應到控制項，因為附加至控制項的多個物件或任何其他視窗，會導致訊息對應中的混淆。

您可以使用這個物件來呼叫控制項物件的任何成員函式。 這類呼叫會影響對話方塊中的控制項。 例如，針對類型的變數 *m_Checkbox*所代表的核取方塊控制項， `CButton` 您可以呼叫：

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

在此，成員變數 *m_Checkbox* 的用途與 `GetMyCheckbox` 在 [不含程式碼嚮導的控制項型別安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)中顯示的成員函式相同。 如果核取方塊不是 [自動] 核取方塊，當您按一下按鈕時，您的對話方塊類別中仍需要 BN_CLICKED 控制通知訊息的處理常式。

如需控制項的詳細資訊，請參閱 [控制項](../mfc/controls-mfc.md)。

## <a name="see-also"></a>另請參閱

[對話方塊中控制項的型別安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[無程式碼嚮導的控制項型別安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)
