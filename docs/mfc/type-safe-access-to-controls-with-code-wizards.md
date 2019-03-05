---
title: 使用程式碼精靈的控制項類型安全存取
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: bf3ecf3016fcc15bd4ada7a15208acd9a04ca0a8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263802"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>使用程式碼精靈的控制項類型安全存取

如果您已熟悉使用 DDX 功能，您可以使用中的控制項屬性[加入成員變數精靈](../ide/add-member-variable-wizard.md)建立型別安全存取。 這個方法很容易建立不使用程式碼精靈的控制項。

如果您只想要存取控制項的值，DDX 會提供它。 如果您想要多個存取控制項的值，請將適當的類別的成員變數新增至您的對話方塊類別中使用加入成員變數精靈。 將此成員變數附加到控制項屬性。

成員變數可以有的控制項屬性，而非值屬性。 [值] 屬性是指傳回的資料類型從控制項，例如`CString`或是**int**。控制項屬性可讓您透過其類型是其中一個控制項類別，在 MFC 中，這類的資料成員的直接存取`CButton`或`CEdit`。

> [!NOTE]
>  對於指定的控制項，如果您想，就可以使用的屬性值和最多與控制項屬性的一個成員變數的多個成員變數。 您可以只有一個對應到控制項，因為多個物件附加至控制項或任何其他視窗中，會導致模稜兩可的訊息對應中的 MFC 物件。

您可以使用這個物件的控制項物件呼叫任何成員函式。 這類呼叫會影響在對話方塊中的控制項。 例如，核取方塊控制項變數代表*m_Checkbox*，型別的`CButton`，您可以呼叫：

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

這裡的成員變數*m_Checkbox*有相同的用途為成員函式`GetMyCheckbox`所示[程式碼精靈而不需要的控制項型別安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)。 如果核取方塊不會自動核取方塊，您仍需要處理常式 BN_CLICKED 控制項通知訊息的對話方塊類別中按一下按鈕時。

如需控制項的詳細資訊，請參閱[控制項](../mfc/controls-mfc.md)。

## <a name="see-also"></a>另請參閱

[對話方塊中之控制項的型別安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[不使用程式碼精靈的控制項型別安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)
