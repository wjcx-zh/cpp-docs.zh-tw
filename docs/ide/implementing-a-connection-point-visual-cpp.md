---
title: 實作連接點 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b75bf145da401ad9889353a1e65448831c602c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-a-connection-point-visual-c"></a>實作連接點 (Visual C++)
若要實作連接點使用實作連接點精靈，您必須已建立專案做為 ATL COM 應用程式，或包含 ATL 支援的 MFC 應用程式。 您可以使用[ATL 專案精靈](../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[MFC 應用程式中加入 ATL 物件](../mfc/reference/adding-atl-support-to-your-mfc-project.md)實作 MFC 應用程式的 ATL 支援。  
  
> [!NOTE]
>  實作 MFC 專案的連接點的詳細資訊，請參閱[連接點](../mfc/connection-points.md)。  
  
 一旦您建立專案，以實作連接點，您必須先加入 ATL 物件。 請參閱[將物件和控制項加入 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)精靈，可將物件加入至您的 ATL 專案的清單。  
  
> [!NOTE]
>  精靈不支援 ATL 對話方塊，建立以 ATL Server 效能物件的效能計數器的 XML Web 服務。  
  
 可連接物件 （也就是來源） 可以為每個外寄的介面公開連接點。 每個輸出介面可以實作的物件 （也就是接收） 上的用戶端。 如需詳細資訊，請參閱[ATL 連接點](../atl/atl-connection-points.md)。  
  
### <a name="to-implement-a-connection-point"></a>若要實作連接點  
  
1.  在 類別檢視，以滑鼠右鍵按一下 ATL 物件的類別名稱。  
  
2.  按一下**新增**從捷徑功能表，然後再按一下**加入連接點**顯示[實作連接點精靈](../ide/implement-connection-point-wizard.md)。  
  
3.  選取適當的型別程式庫實作，並按一下 連接點介面**完成**。  
  
4.  在 類別檢視，檢查每個連接點所建立的 proxy 類別。 類別會顯示為 CProxy*InterfaceName*\<T >，以及衍生自[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)。  
  
5.  按兩下要顯示的連接點類別定義的連接點類別。  
  
    -   如果您實作您自己的專案介面的連接點，就會出現下列定義  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         如果您實作的本機介面，方法和屬性出現在類別主體中。  
  
    -   如果您實作連接點的另一個介面，定義包含介面的方法，每一個前面加上`Fire_`。  
  
## <a name="see-also"></a>另請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [將連接點新增至物件](../atl/adding-connection-points-to-an-object.md)