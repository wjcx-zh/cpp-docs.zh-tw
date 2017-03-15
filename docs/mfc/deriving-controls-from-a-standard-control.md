---
title: "從標準控制項衍生控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通用控制項 [C++], 衍生自"
  - "控制項 [MFC], 衍生"
  - "衍生控制項"
  - "標準控制項"
  - "標準控制項, 衍生控制項來源"
  - "Windows 通用控制項 [C++], 衍生自"
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 從標準控制項衍生控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

與任何 [CWnd](../mfc/reference/cwnd-class.md) 衍生類別，您可以從現有控制項類別衍生新類別以修改控制項行為。  
  
### 建立衍生的控制項類別  
  
1.  從現有的控制項類別衍生您的類別並選擇性地覆寫 **Create** 成員函式，以便提供必要的引數給基底類別 **Create** 函式。  
  
2.  提供訊息處理常式成員函式和訊息對應項以修改控制項行為以回應特定 Windows 訊息。  請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
3.  提供新的成員函式以擴充控制項的功能 \(選擇項\)。  
  
 使用對話方塊中的衍生控制項需要額外的工作。  對話方塊中的控制項的型別和位置通常指定於對話方塊樣板資源。  如果您建立衍生的控制項類別，您不可以在對話方塊樣板指定它，因為資源編譯器不知道您的衍生類別。  
  
#### 將衍生的控制項置於對話方塊  
  
1.  將衍生的控制項類別的物件內嵌在您的衍生對話方塊類別的宣告。  
  
2.  覆寫您的對話方塊類別的 `OnInitDialog` 成員函式以呼叫衍生控制項的 `SubclassDlgItem` 成員函式。  
  
 `SubclassDlgItem` 「動態子類別」從對話方塊樣板建立的控制項。  當控制項動態子類別化時，您將之掛勾於 Windows，處理應用程式中的某些訊息，然後再傳遞剩餘的訊息到 Windows。  如需詳細資訊，請參閱類別 `CWnd` 的 [SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md) 成員函式於 *MFC 參考*。  下列範例顯示如何寫入呼叫 `SubclassDlgItem` 的 `OnInitDialog` 覆寫:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/CPP/deriving-controls-from-a-standard-control_1.cpp)]  
  
 由於衍生的控制項在對話方塊類別中的，它會在建構對話方塊時建構，因此會當終結對話方塊時終結。  在 [手動加入控制項](../mfc/adding-controls-by-hand.md)的範例比較這個程式碼。  
  
## 請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)