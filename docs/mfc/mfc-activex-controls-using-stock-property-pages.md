---
title: MFC ActiveX 控制項：使用內建屬性頁
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: 13a0edb72657c9ffad00dcb909019bdfe4b87e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358206"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控制項：使用內建屬性頁

本文討論 ActiveX 控件可用的股票屬性頁以及如何使用它們。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

有關在 ActiveX 控制件中使用屬性頁的詳細資訊,請參閱以下文章:

- [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控制項：加入另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC 提供三個用於 ActiveX 控制`CLSID_CColorPropPage`的`CLSID_CFontPropPage`庫存`CLSID_CPicturePropPage`屬性頁: 與 。 這些頁面分別顯示股票顏色、字體和圖片屬性的用戶介面。

要將這些屬性頁合併到控制項中,請將其 ID 添加到初始化控制件的屬性頁 ID 數位的代碼中。 在下面的範例中,此代碼位於控件實現檔中 (。CPP),初始化陣列以包含所有三個股票屬性頁和預設屬性頁(在此範例中命名`CMyPropPage`):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

請注意,BEGIN_PROPPAGEIDS宏中的屬性頁的計數為 4。 這表示 ActiveX 控件支援的屬性頁數。

進行這些修改後,重新生成專案。 控制項現在具有字體、圖片和顏色屬性的屬性頁。

> [!NOTE]
> 如果無法存取控制項庫存屬性頁,可能是因為 MFC DLL (MFCxx.DLL) 尚未與當前操作系統正確註冊。 這通常是由於在不同於當前運行的操作系統下安裝 Visual C++。

> [!TIP]
> 如果股票屬性頁不可見(請參閱上一條註釋),請從具有 DLL 完整路徑名稱的命令列中運行 RegSvr32.exe 來註冊 DLL。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：新增內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)
