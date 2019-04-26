---
title: 不使用程式碼精靈的控制項類型安全存取
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 5b4b604bf42a327edf3ac7a83dcfc42a5e0d8c54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180807"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>不使用程式碼精靈的控制項類型安全存取

要建立類型安全存取控制項的第一個方法就是使用內嵌成員函式，將類別 `CWnd` 的 `GetDlgItem` 成員函式的傳回類型轉換為適當的 C++ 控制項類型，如下列範例所示：

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

接著您可以使用這個成員函式，透過與下列類似的程式碼，以類型安全的方式來存取控制項：

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>另請參閱

[對話方塊中之控制項的型別安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[使用程式碼精靈的控制項型別安全存取](../mfc/type-safe-access-to-controls-with-code-wizards.md)
