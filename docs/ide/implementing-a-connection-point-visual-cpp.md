---
title: "實作連接點 (Visual C++) | Microsoft Docs"
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
  - "連接點 [C++], 實作"
  - "實作連接點精靈 [C++]"
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實作連接點 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用實作連接點精靈來實作連接點 \(Connection Point\)，您必須先將專案建立為 ATL COM 應用程式或是包含 ATL 支援的 MFC 應用程式。  您可以使用 [ATL 專案精靈](../atl/reference/atl-project-wizard.md)來建立 ATL 應用程式，或[將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)來為 MFC 應用程式實作 ATL 支援。  
  
> [!NOTE]
>  如需為 MFC 專案實作連接點的詳細資訊，請參閱[連接點](../mfc/connection-points.md)。  
  
 建立專案之後，您必須先加入 ATL 物件才能實作連接點。  如需將物件加入至 ATL 專案的精靈清單，請參閱[將物件和控制項加入至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
> [!NOTE]
>  精靈不支援 ATL 對話方塊、用 ATL Server 建立的 XML Web Service、效能物件或效能計數器。  
  
 可連接物件 \(Connectable Object\)，也就是來源，可為其每個輸出介面公開連接點。  每個輸出介面都可由物件上的用戶端 \(也就是接收\) 來實作。  如需詳細資訊，請參閱 [ATL 連接點](../atl/atl-connection-points.md)。  
  
### 若要實作連接點  
  
1.  在 \[類別檢視\] 中，以滑鼠右鍵按一下 ATL 物件的類別名稱。  
  
2.  從捷徑功能表按一下 \[加入\]，接著按一下 \[加入連接點\] 以顯示[實作連接點精靈](../ide/implement-connection-point-wizard.md)。  
  
3.  從適當的型別程式庫選取要實作的連接點介面，接著按一下 \[完成\]。  
  
4.  在 \[類別檢視\] 中，檢查為每個連接點建立的 Proxy 類別。  這些類別出現為 CProxy*InterfaceName*\<T\>，而且衍生自 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)。  
  
5.  按兩下連接點類別以顯示連接點類別的定義。  
  
    -   如果您是為自己專案的介面實作連接點，則會出現以下定義：  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         如果您實作本機介面，則方法和屬性會出現在類別主體。  
  
    -   如果您為其他介面實作連接點，則定義會包含介面的方法，每個方法之前都會加上 `Fire_`。  
  
## 請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Adding Connection Points to an Object](../atl/adding-connection-points-to-an-object.md)