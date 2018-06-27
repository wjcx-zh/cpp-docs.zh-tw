---
title: 使用程式碼精靈的控制項類型安全存取 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f86a8f22bae990261be5150755a26d50d4bef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950457"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>使用程式碼精靈的控制項類型安全存取
如果您熟悉 DDX 功能，您可以使用中的控制項屬性[加入成員變數精靈](../ide/add-member-variable-wizard.md)建立類型安全存取。 這個方法會比建立不使用程式碼精靈的控制項容易的。  
  
 如果您只想存取控制項的值，DDX 會提供。 如果您想要多個存取控制項的值，請將適當的類別的成員變數新增至您的對話方塊類別中使用加入成員變數精靈。 將此成員變數附加到控制項屬性。  
  
 成員變數都可以有的控制項屬性，而不是值屬性。 Value 屬性是指傳回的資料類型從控制項，例如`CString`或**int**。控制項屬性可讓您透過其類型是 mfc 控制項類別的其中一個這類的資料成員的直接存取`CButton`或`CEdit`。  
  
> [!NOTE]
>  對於指定的控制項，您可以如果您想，有多個成員變數與值屬性，最多一個成員變數與控制項屬性。 您可以有只有一個對應至控制項，因為多個物件附加至控制項或任何其他視窗，這樣會導致訊息對應中的模稜兩可的 MFC 物件。  
  
 您可以使用此物件的控制項物件呼叫任何成員函式。 這類呼叫會影響在對話方塊中的控制項。 例如，核取方塊控制項的變數代表*m_Checkbox*，型別`CButton`，您可以呼叫：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 這裡的成員變數*m_Checkbox*有相同的用途為成員函式`GetMyCheckbox`示[類型安全存取控制項沒有程式碼精靈](../mfc/type-safe-access-to-controls-without-code-wizards.md)。 如果核取方塊不是自動核取方塊，您仍必須處理常式 BN_CLICKED 控制項通知訊息的對話方塊類別中按一下按鈕時。  
  
 如需將控制項的詳細資訊，請參閱[控制項](../mfc/controls-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊中的控制項類型安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [不使用程式碼精靈的控制項型別安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)

