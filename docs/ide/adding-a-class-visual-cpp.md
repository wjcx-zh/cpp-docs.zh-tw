---
title: 新增類別 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.adding
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14e16d8b5c15939adb792a96a828bafd07ba4041
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33333280"
---
# <a name="adding-a-class-visual-c"></a>加入類別 (Visual C++)
若要在 Visual C++ 專案中新增類別，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後依序按一下 [新增] 和 [類別]。 這會開啟 [[新增類別] 對話方塊](../ide/add-class-dialog-box.md)。  
  
 當您新增類別時，您必須指定與 MFC 或 ATL 中已存在類別不同的名稱。 如果您指定的名稱已存在於任一程式庫中，IDE 會顯示錯誤訊息。  
  
 如果您的專案命名慣例要求您使用現有的名稱，因為 C++ 會區分大小寫，所以您可以只變更名稱中一或多個字母的大小寫。 例如，雖然您不可以將類別命名為 `CDocument`，但您可以將它命名為 `cdocument`。  
  
## <a name="what-kind-of-class-do-you-want-to-add"></a>您想要新增哪種類別？  
 在 [新增類別] 對話方塊中，當您展開左窗格中的 [Visual C++] 節點時，即會顯示已安裝範本的數個群組。 這些群組包含 **CLR**、**ATL**、**MFC** 和 **C++**。 當您選取群組時，中間窗格會顯示該群組中的可用範本清單。 每個範本包含類別所需的檔案和原始程式碼。  
  
 若要產生新的類別，請在中間窗格中選取範本，在 [名稱] 方塊中鍵入類別名稱，然後按一下 [新增]。 這會開啟 [新增類別精靈]，以供您指定類別的選項。  
  
-   如需如何建立 MFC 類別的詳細資訊，請參閱 [MFC 類別](../mfc/reference/adding-an-mfc-class.md)。  
  
-   如需如何建立 ATL 類別的詳細資訊，請參閱 [ATL 簡易物件](../atl/reference/adding-an-atl-simple-object.md)。  
  
> [!NOTE]
>  [將 ATL 支援新增至 MFC] 範本不會建立類別，而是設定專案使用 ATL。 如需詳細資訊，請參閱 [MFC 專案中的 ATL 支援](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
 若要建立不使用 MFC、ATL 或 CLR 的 C++ 類別，請使用已安裝範本之 **C++** 群組中的 [C++ 類別] 範本。 如需詳細資訊，請參閱[新增泛型 C++ 類別](../ide/adding-a-generic-cpp-class.md)。  
  
 表單架構的 C++ 類別有兩種。 第一種是 [CFormView 類別](../mfc/reference/cformview-class.md)，可建立 MFC 類別。 第二種可建立 CLR Windows Forms 類別。  
  
## <a name="see-also"></a>請參閱  
 [建立表單架構的 MFC 應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [新增類別對話方塊](../ide/add-class-dialog-box.md)   
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)