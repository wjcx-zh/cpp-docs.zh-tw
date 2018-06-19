---
title: 將多個檢視加入至單一文件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb40b356b5601e19c33083c7b731a1dc411de3c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344145"
---
# <a name="adding-multiple-views-to-a-single-document"></a>將多個檢視加入至單一文件
在建立使用 Microsoft Foundation Class (MFC) 程式庫的單一文件介面 (SDI) 應用程式，每個文件類型為單一檢視類型相關聯。 在某些情況下，最好能夠切換文件的新檢視目前的檢視。  
  
> [!TIP]
>  如需實作單一文件的多個檢視的其他程序，請參閱[CDocument::AddView](../mfc/reference/cdocument-class.md#addview)和[收集](../visual-cpp-samples.md)MFC 範例。  
  
 您可以實作這項功能，透過新增`CView`-衍生的類別和其他程式碼以動態方式將檢視切換到現有的 MFC 應用程式。  
  
 步驟如下所示：  
  
-   [修改現有的應用程式類別](#vcconmodifyexistingapplicationa1)  
  
-   [建立和修改新的檢視類別](#vcconnewviewclassa2)  
  
-   [建立並附加新的檢視](#vcconattachnewviewa3)  
  
-   [實作切換函式](#vcconswitchingfunctiona4)  
  
-   [加入切換檢視的支援](#vcconswitchingtheviewa5)  
  
 本主題的其餘部分會假設下列：  
  
-   名稱`CWinApp`-衍生的物件是`CMyWinApp`，和`CMyWinApp`宣告，然後在 MYWINAPP 中定義。H 和 MYWINAPP。CPP。  
  
-   `CNewView` 是的新名稱`CView`-衍生物件，和`CNewView`宣告，然後在 NEWVIEW 中定義。H 和 NEWVIEW。CPP。  
  
##  <a name="vcconmodifyexistingapplicationa1"></a> 修改現有的應用程式類別  
 檢視之間切換應用程式，您要加入成員變數來儲存檢視表，並將其切換的方法來修改應用程式類別。  
  
 將下列程式碼加入至宣告`CMyWinApp`MYWINAPP 中。H:  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]  
  
 新的成員變數，`m_pOldView`和`m_pNewView`，指向目前的檢視及新建的一個。 新的方法 (`SwitchView`) 切換檢視，當使用者要求。 在本主題中稍後討論方法主體[實作切換函式](#vcconswitchingfunctiona4)。  
  
 上次修改應用程式類別需要包括定義 Windows 訊息的新標頭檔 (**WM_INITIALUPDATE**) 切換函式中使用。  
  
 包含部分 MYWINAPP 中插入下列這行。CPP:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 儲存變更並繼續下一個步驟。  
  
##  <a name="vcconnewviewclassa2"></a> 建立和修改新的檢視類別  
 建立新的檢視類別更容易使用**新類別**類別檢視中可用的命令。 這個類別的唯一需求是其衍生自`CView`。 將這個新類別加入至應用程式。 如需將新類別加入至專案的特定資訊，請參閱[將類別加入](../ide/adding-a-class-visual-cpp.md)。  
  
 一旦您將類別加入至專案，您需要變更某些檢視類別成員的存取範圍。  
  
 修改 NEWVIEW。藉由變更從的存取規範 H`protected`至**公用**建構函式和解構函式。 這可讓類別來建立和摧毀動態和修改的檢視外觀，才能顯示。  
  
 儲存變更並繼續下一個步驟。  
  
##  <a name="vcconattachnewviewa3"></a> 建立並附加新的檢視  
 若要建立並附加新的檢視，您需要修改`InitInstance`函式的應用程式類別。 修改加入新的程式碼會建立新的檢視物件，然後初始化這兩個`m_pOldView`和`m_pNewView`與兩個現有的檢視物件。  
  
 因為內建立新的檢視`InitInstance`函式，這兩個新的和現有檢視保存應用程式的存留期間。 不過，應用程式可以輕鬆地以動態方式建立新的檢視。  
  
 插入這個程式碼的呼叫後方`ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 儲存變更並繼續下一個步驟。  
  
##  <a name="vcconswitchingfunctiona4"></a> 實作切換函式  
 在上一個步驟中，您可以加入程式碼，建立並初始化新的檢視物件。 實作切換的方法，為最後的主要部分`SwitchView`。  
  
 在您的應用程式的實作檔結尾類別 (MYWINAPP。CPP)，加入下列方法定義：  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 儲存變更並繼續下一個步驟。  
  
##  <a name="vcconswitchingtheviewa5"></a> 加入切換檢視的支援  
 最後一個步驟牽涉到將呼叫的程式碼加入`SwitchView`方法，當應用程式需要檢視之間切換。 這可以數種方式完成： 透過加入新的功能表項目，讓使用者選擇或在符合特定條件時，內部切換檢視。  
  
 如需將加入新的功能表項目和命令處理常式函式的詳細資訊，請參閱[命令和控制項告知處理常式](../mfc/handlers-for-commands-and-control-notifications.md)。  
  
## <a name="see-also"></a>另請參閱  
 [文件/檢視架構](../mfc/document-view-architecture.md)

