---
title: 實作連接點 (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 45e3dfcfc7e7bcb9fcbe14e08a8c238fe9bec5a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568320"
---
# <a name="implementing-a-connection-point-visual-c"></a>實作連接點 (Visual C++)

若要使用 [實作連接點精靈] 實作連接點，您必須已將專案建立作為 ATL COM 應用程式，或作為包含 ATL 支援的 MFC 應用程式。 您可以使用 [ATL 專案精靈](../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[將 ALT 物件新增至 MFC 應用程式](../mfc/reference/adding-atl-support-to-your-mfc-project.md)，以實作 MFC 應用程式的 ATL 支援。

> [!NOTE]
>  如需實作 MFC 專案連接點的詳細資訊，請參閱[連接點](../mfc/connection-points.md)。

建立專案之後，若要實作連接點，您必須先新增 ATL 物件。 請參閱[將物件和控制項新增至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)，以取得將物件新增至 ATL 專案的清單。

> [!NOTE]
>  精靈不支援 ATL 對話方塊、以 ATL Server 建立的 XML Web 服務、效能物件或效能計數器。

可連接物件 (也就是來源) 可以為每個輸出介面公開連接點。 每個輸出介面都可以由物件上的用戶端 (也就是接收，sink) 所實作。 如需詳細資訊，請參閱 [ATL 連接點](../atl/atl-connection-points.md)。

### <a name="to-implement-a-connection-point"></a>實作連接點

1. 在 [類別檢視] 中，以滑鼠右鍵按一下 ATL 物件的類別名稱。

1. 從捷徑功能表按一下 [新增]，然後按一下 [新增連接點]，顯示[實作連接點精靈](../ide/implement-connection-point-wizard.md)。

1. 從適當的型別程式庫選取要實作的連接點介面，然後按一下 [完成]。

1. 在 [類別檢視] 中，檢查為每個連接點所建立的 Proxy 類別。 類別會顯示為 CProxy*InterfaceName*\<T>，且為衍生自 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)。

1. 按兩下連接點類別，以顯示連接點類別的定義。

   - 如果您實作自己專案介面的連接點，就會出現下列定義

        ```
        template< class T >
        class CProxyInterfaceName :
           public IConnectionPointImpl< T, &IID_InterfaceName >
        {
        public:
        };
        ```

         If you implement a local interface, methods and properties appear in the class body.

   - 如果您實作另一個介面的連接點，定義會包含介面的方法，每一個前面加上 `Fire_`。

## <a name="see-also"></a>請參閱

[使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[將連接點新增至物件](../atl/adding-connection-points-to-an-object.md)