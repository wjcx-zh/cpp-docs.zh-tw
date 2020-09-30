---
title: 從類型程式庫加入 MFC 類別
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: 45bad00155cc1587980e6f3b25843a7a22e7e754
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503040"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別

您可以使用此嚮導，從可用類型程式庫中的介面建立 MFC 類別。 您可以將 MFC 類別新增至 [MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../../mfc/reference/creating-an-mfc-activex-control.md)。

> [!NOTE]
> 您不需要建立啟用自動化的 MFC 專案，就可以從類型程式庫加入類別。

類型程式庫包含元件所公開介面的二進位描述、定義方法及其參數和傳回類型。 您的類型程式庫必須註冊，才能出現在 [從 Typelib 新增類別的類別] 清單中的 [ **可用的型別程式庫** ] 清單中。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別

1. 在 **方案總管** 或 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下您要新增類別的專案名稱。

1. 從捷徑功能表按一下 [新增]****，然後按一下 [新增類別]****。

1. 在 [ [加入類別](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) ] 對話方塊的 [範本] 窗格中，按一下 [ **來自 Typelib 的 MFC 類別**]，然後按一下 [ **開啟** ]，以顯示 [ [從 typelib Wizard 加入類別]](../../mfc/reference/add-class-from-typelib-wizard.md)。

在嚮導中，您可以在類型程式庫中加入一個以上的類別。 同樣地，您可以在單一 wizard 會話中，從一個以上的類型程式庫加入類別。

此 wizard 會針對您從選取的類型程式庫新增的每個介面，建立衍生自 [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)的 MFC 類別。 `COleDispatchDriver` 執行 OLE automation 的用戶端。

## <a name="see-also"></a>另請參閱

[Automation 用戶端](../../mfc/automation-clients.md)<br/>
[Automation 用戶端：使用類型程式庫](../../mfc/automation-clients-using-type-libraries.md)
