---
title: "使用程式碼精靈的控制項類型安全存取 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "程式碼精靈"
  - "DDX (對話資料交換), 存取控制項"
  - "對話方塊控制項, 存取"
  - "對話方塊, 存取控制項"
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用程式碼精靈的控制項類型安全存取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您熟悉 DDX 功能，您可以使用 [加入成員變數精靈](../ide/add-member-variable-wizard.md) 控制項屬性的型別安全存取。  這個方法會建立控制項容易沒有程式碼精靈。  
  
 如果您要控制值的存取， DDX 提供它。  如果您要不僅存取控制項的值，請使用加入成員變數精靈加入適當類別的成員變數加入至對話方塊類別。  此成員變數給控制項屬性。  
  
 成員變數可能有控制項屬性 \(而不是屬性的值。  Value 屬性是指從控制項傳回的資料型別，例如 `CString` 或 `int`。  控制項屬性透過型別是一個 MFC 控制項類別，例如 `CButton` 或 `CEdit`資料成員啟用對控制項的直接存取。  
  
> [!NOTE]
>  如需特定控制項，您可以，因此，如果您需要，具有值的屬性的多個成員變數和最多與控制項屬性的 10% 成員變數。  因為多個物件附加至控制項，或其他視窗，會導致訊息對應，模稜兩可的情況。您只能將 MFC 物件會對應至控制項。  
  
 您可以使用這個物件呼叫控制物件的所有成員函式。  此呼叫會影響在對話方塊的控制項。  例如，，以變數 `m_Checkbox`代表的核取方塊控制項， `CButton`型別，您可以呼叫:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/CPP/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 此成員變數 `m_Checkbox` 為用途和成員函式在 [對控制項的型別安全存取沒有程式碼精靈](../mfc/type-safe-access-to-controls-without-code-wizards.md)中顯示的 `GetMyCheckbox` 。  如果核取方塊不是自動核取方塊，則 **BN\_CLICKED** 控制通知訊息的對話方塊類別會需要處理常式，在按一下按鈕時。  
  
 如需控制項的詳細資訊，請參閱 [控制項](../mfc/controls-mfc.md)。  
  
## 請參閱  
 [對話方塊中之控制項的類型安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [不使用程式碼精靈的控制項類型安全存取](../mfc/type-safe-access-to-controls-without-code-wizards.md)