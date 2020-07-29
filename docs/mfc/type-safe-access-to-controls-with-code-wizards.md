---
title: 使用程式碼精靈的控制項類型安全存取
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: bfbc27dbcdeeb38c40f5d989bacd65a23198d4f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213966"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>使用程式碼精靈的控制項類型安全存取

如果您熟悉 DDX 功能，您可以使用 [[加入成員變數] Wizard](../ide/add-member-variable-wizard.md)中的控制項屬性來建立型別安全存取。 這種方法比建立不含程式碼的控制項更容易。

如果您只想要存取控制項的值，DDX 會提供它。 如果您想要執行的不只是存取控制項的值，請使用 [加入成員變數] Wizard，將適當類別的成員變數新增至對話方塊類別。 將此成員變數附加至控制項屬性。

成員變數可以有控制項屬性，而不是 Value 屬性。 Value 屬性會參考從控制項傳回的資料類型，例如 `CString` 或 **`int`** 。 控制項屬性可讓您透過類型為 MFC 中的其中一個控制項類別（例如或）的資料成員，直接存取控制項 `CButton` `CEdit` 。

> [!NOTE]
> 針對指定的控制項，如果您想要的話，可以有多個具有 Value 屬性的成員變數，以及一個具有控制項屬性的成員變數。 您只能有一個對應至控制項的 MFC 物件，因為附加至控制項或任何其他視窗的多個物件，會導致訊息對應中出現不明確的情況。

您可以使用這個物件來呼叫控制項物件的任何成員函式。 這類呼叫會影響對話方塊中的控制項。 例如，針對類型的變數*m_Checkbox*所代表的核取方塊控制項， `CButton` 您可以呼叫：

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

在這裡，成員變數*m_Checkbox*的用途與成員函式相同， `GetMyCheckbox` [但不含程式碼的存取權會](../mfc/type-safe-access-to-controls-without-code-wizards.md)顯示在控制項的「安全的存取控制」中。 如果核取方塊不是 [自動] 核取方塊，當您按一下按鈕時，您仍然需要 BN_CLICKED 控制項通知訊息的對話方塊類別中的處理常式。

如需控制項的詳細資訊，請參閱[控制項](../mfc/controls-mfc.md)。

## <a name="see-also"></a>另請參閱

[對話方塊中控制項的型別安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[不使用程式碼嚮導之控制項的型別安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)
