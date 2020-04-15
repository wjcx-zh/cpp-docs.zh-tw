---
title: 從類型程式庫加入 MFC 類別
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: bf9c763a215a4880d5b0ad206f6a347341fea9eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371714"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別

使用此嚮導可以從可用類型庫中的介面創建 MFC 類。 您可以將 MFC 類別新增至 [MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../../mfc/reference/creating-an-mfc-activex-control.md)。

> [!NOTE]
> 無需在啟用自動化功能後創建 MFC 專案,即從類型庫中添加類。

類型庫包含元件公開的介面的二進位描述,定義方法及其參數和返回類型。 必須註冊類型庫才能顯示在「從 Typelib 精靈添加類」**的 「可用類型庫**」 清單中。 有關詳細資訊,請參閱 MSDN 庫中的「內部分散式 COM:類型庫和語言集成」。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>從類型庫加入 MFC 類別

1. 在**解決方案資源管理器**或[類檢視中](/visualstudio/ide/viewing-the-structure-of-code),右鍵單擊要向其添加類的專案的名稱。

1. 從捷徑功能表按一下 [新增]****，然後按一下 [新增類別]****。

1. 在[「新增類別」](../../ide/add-class-dialog-box.md)對話框中,在「樣本」窗格中,按下**Typelib 中的 MFC 類別**,然後按下 **「打開」** 以顯示[「從 Typelib 嚮導添加類](../../mfc/reference/add-class-from-typelib-wizard.md)」 。

在嚮導中,可以在類型庫中添加多個類。 同樣,您可以在單個嚮導會話中從多個類型庫中添加類。

該嚮導為從所選類型庫添加的每個介面創建一個 MFC 類,該類派生自[COleDispatchDriver。](../../mfc/reference/coledispatchdriver-class.md) `COleDispatchDriver`實現 OLE 自動化的用戶端。

## <a name="see-also"></a>另請參閱

[Automation 用戶端](../../mfc/automation-clients.md)<br/>
[Automation 用戶端：使用型別程式庫](../../mfc/automation-clients-using-type-libraries.md)
