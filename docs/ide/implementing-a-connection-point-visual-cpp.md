---
title: 實作連接點
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.cp.overview
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 7afa61246c5251936967e281f7237dc37e5be045
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693278"
---
# <a name="implement-a-connection-point"></a>實作連接點

若要使用 [實作連接點精靈] 實作連接點，您必須已將專案建立作為 ATL COM 應用程式，或作為包含 ATL 支援的 MFC 應用程式。 您可以使用 [ATL 專案精靈](../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[將 ALT 物件新增至 MFC 應用程式](../mfc/reference/adding-atl-support-to-your-mfc-project.md)，以實作 MFC 應用程式的 ATL 支援。

> [!NOTE]
> 如需實作 MFC 專案連接點的資訊，請參閱[連接點](../mfc/connection-points.md)。

建立專案之後，若要實作連接點，您必須先新增 ATL 物件。 請參閱[將物件和控制項新增至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)，以取得將物件新增至 ATL 專案的精靈清單。

> [!NOTE]
> 精靈不支援 ATL 對話方塊、以 ATL Server 建立的 XML Web 服務、效能物件或效能計數器。

可連接物件 (也就是來源) 可以為每個輸出介面顯示連接點。 每個輸出介面都可以由物件上的用戶端 (也就是接收，sink) 所實作。 如需詳細資訊，請參閱 [ATL 連接點](../atl/atl-connection-points.md)。

**實作連接點：**

1. 在 [類別檢視] 中，以滑鼠右鍵按一下 ATL 物件的類別名稱。

1. 從捷徑功能表選擇 [新增]，然後選擇 [新增連接點] 以顯示[實作連接點精靈](#implement-connection-point-wizard)。

1. 從適當的型別程式庫選取要實作的連接點介面，然後選取 [完成]。

1. 在 [類別檢視] 中，檢查為每個連接點所建立的 Proxy 類別。 類別會顯示為 CProxy*InterfaceName*\<T>，且為衍生自 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)。

1. 按兩下連接點類別，以顯示連接點類別的定義。

   - 如果您實作自己專案介面的連接點，就會出現下列定義：

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - 如果您實作本機介面，方法和屬性會出現在類別主體中。

   - 如果您實作另一個介面的連接點，定義會包含介面的方法，每一個前面加上 `Fire_`。

## <a name="in-this-section"></a>本節內容

- [實作連接點精靈](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>實作連接點精靈

這個精靈會實作 COM 物件的連接點。 可連接物件 (也就是來源) 可以為本身的介面或任何輸出介面顯示連接點。 Visual C++ 和 Windows 都提供具有輸出介面的型別程式庫。 每個輸出介面都可以由物件上的用戶端 (也就是接收，sink) 所實作。

如需詳細資訊，請參閱 [ATL 連接點](../atl/atl-connection-points.md)。

- **可用的型別程式庫**

  顯示可用的型別程式庫，其中保存您可以為其實作連接點的介面定義。 選取省略符號按鈕，找出具有要使用之型別程式庫的檔案。

- **位置**

  顯示 [可用的型別程式庫] 清單中目前選取之型別程式庫的位置。

- **介面**

  顯示介面，其定義保存在 [可用的型別程式庫] 方塊中目前選取的型別程式庫內。

  |傳輸按鈕|描述|
  |---------------------|-----------------|
  |**>**|將 [介面] 清單中目前選取的介面名稱新增至 [實作連接點] 清單。|
  |**>>**|將 [介面] 清單中所有可用介面名稱新增至 [實作連接點] 清單。|
  |**\<**|移除 [實作連接點] 清單中目前選取的介面名稱。|
  |**\<\<**|移除 [實作連接點] 清單中目前列出的所有介面名稱。|

- **實作連接點**

  當您選取 [完成] 時，顯示您實作其連接點的介面名稱。
