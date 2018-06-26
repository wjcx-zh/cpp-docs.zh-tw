---
title: 從標準控制項衍生控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4ae7fb09e1f453b6d7bc82a7fb038567809f872
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932243"
---
# <a name="deriving-controls-from-a-standard-control"></a>從標準控制項衍生控制項
如同使用任何[CWnd](../mfc/reference/cwnd-class.md)-衍生的類別，您可以從現有的控制項類別衍生新類別，以修改控制項的行為。  
  
### <a name="to-create-a-derived-control-class"></a>建立衍生的控制項類別  
  
1.  從現有的控制項類別衍生您的類別，並選擇性地覆寫`Create`，使其提供需要的引數給基底類別成員函式`Create`函式。  
  
2.  提供訊息處理常式成員函式和訊息對應項目以修改控制項在回應特定 Windows 訊息時的行為。 請參閱[將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
3.  提供新的成員函式以擴充控制項的功能 (選擇性)。  
  
 在對話方塊中使用衍生的控制項需要進行額外的工作。 對話方塊中控制項的類型和位置通常是在對話方塊範本資源中指定。 如果您建立一個衍生的控制項類別，則不可以在對話方塊範本中指定該控制項類別，因為資源編譯器並不知道您的衍生類別相關資訊。  
  
#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>將衍生的控制項置於對話方塊中  
  
1.  將衍生控制項類別的物件內嵌在您的衍生對話方塊類別宣告中。  
  
2.  在您的對話方塊類別中覆寫 `OnInitDialog` 成員函式以呼叫衍生控制項的 `SubclassDlgItem` 成員函式。  
  
 `SubclassDlgItem` 會「動態子類別化」從對話方塊範本建立的控制項。 當控制項進行動態子類別化時，表示您將其與 Windows 連結、處理應用程式中的某些訊息，然後再將其餘的訊息傳遞到 Windows。 如需詳細資訊，請參閱[SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem)類別成員函式`CWnd`中*MFC 參考*。 下列範例說明如何撰寫用於呼叫 `OnInitDialog` 的 `SubclassDlgItem` 覆寫：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]  
  
 由於衍生的控制項是內嵌在對話方塊類別中，因此會在建構對話方塊時建構該控制項，所以也會在終結對話方塊時終結該控制項。 比較這個程式碼中的範例[手動加入控制項](../mfc/adding-controls-by-hand.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)

