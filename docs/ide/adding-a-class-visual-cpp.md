---
title: "加入類別 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.classes.adding
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ac87368f2bd38c32425799103fa3999dd11b3298
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="adding-a-class-visual-c"></a>加入類別 (Visual C++)
若要新增的類別，在 Visual c + + 專案中，在**方案總管] 中**，以滑鼠右鍵按一下專案，按一下**新增**，然後按一下 [**類別**。 這會開啟[加入類別對話方塊](../ide/add-class-dialog-box.md) 對話方塊。  
  
 當您新增的類別時，您必須指定不同於 MFC 或 ATL 中已存在的類別名稱 如果您指定的名稱已存在於其中一個程式庫時，IDE 會顯示錯誤訊息。  
  
 如果您的專案命名慣例會要求您使用現有的名稱，然後您可以只變更名稱中的一個或多個字母的大小寫因為 c + + 會區分大小寫。 例如，雖然您無法命名類別`CDocument`，您可以將檔案命名`cdocument`。  
  
## <a name="what-kind-of-class-do-you-want-to-add"></a>您要新增什麼類型的類別  
 在**加入類別**對話方塊中，當您展開**Visual c + +**節點會顯示已安裝的範本數個群組的左窗格中。 群組包含**CLR**， **ATL**， **MFC**，和**c + +**。 當您選取的群組時，該群組中的可用範本的清單會顯示在中間窗格中。 每個範本包含的檔案和原始程式碼所需的類別。  
  
 若要產生新的類別，在中間窗格中選取範本中，輸入中的類別名稱**名稱**方塊，然後按一下**新增**。 這會開啟**加入類別精靈**，因此您可以指定類別的選項。  
  
-   如需如何建立 MFC 類別的詳細資訊，請參閱[MFC 類別](../mfc/reference/adding-an-mfc-class.md)。  
  
-   如需如何建立 ATL 類別的詳細資訊，請參閱[ATL 簡單物件](../atl/reference/adding-an-atl-simple-object.md)。  
  
> [!NOTE]
>  範本**加入 ATL 支援加入至 MFC**並不會建立一個類別，但改為設定要使用 ATL 專案 如需詳細資訊，請參閱[MFC 專案中的 ATL 支援](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
 若要讓不使用 MFC，ATL 或 CLR 的 c + + 類別，使用**c + + 類別**中的範本**c + +**群組已安裝的範本。 如需詳細資訊，請參閱[加入泛型 c + + 類別](../ide/adding-a-generic-cpp-class.md)。  
  
 使用兩種類型的表單架構 c + + 類別。 第一個， [CFormView 類別](../mfc/reference/cformview-class.md)建立 MFC 類別。 第二個建立 CLR Windows Form 的類別。  
  
## <a name="see-also"></a>請參閱  
 [建立表單架構的 MFC 應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [加入類別對話方塊](../ide/add-class-dialog-box.md)   
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)