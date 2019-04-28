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
ms.openlocfilehash: b73a027422cfe9cbf03afece400c1b513cace151
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239331"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控制項：使用內建屬性頁

這篇文章討論適用於 ActiveX 控制項和使用方式的內建屬性頁。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

如需有關如何使用 ActiveX 控制項中的 屬性頁的詳細資訊，請參閱下列文章：

- [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控制項：新增另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC ActiveX 控制項用於提供三個內建屬性頁： `CLSID_CColorPropPage`， `CLSID_CFontPropPage`，和`CLSID_CPicturePropPage`。 這些頁面會分別顯示內建的色彩、 字型和圖片屬性的使用者介面。

若要併入控制項中的這些屬性頁，將其識別碼加入初始化的屬性頁 Id 的控制項陣列的程式碼。 在下列範例中，此程式碼，位於控制項實作檔 (。CPP)，初始化陣列，包含所有三個內建屬性頁和 [預設] 屬性頁 (名為`CMyPropPage`在此範例中):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

請注意，屬性頁中，在 BEGIN_PROPPAGEIDS 巨集的計數 4。 這表示 ActiveX 控制項所支援的屬性頁的數目。

在進行這些修改之後，重建您的專案。 您的控制項現在會有字型、 圖片 及 色彩屬性的屬性頁。

> [!NOTE]
>  如果無法存取控制項內建屬性頁，可能是因為 MFC DLL (MFCxx.DLL) 尚未正確註冊與目前的作業系統。 這通常安裝視覺效果的結果C++在不同於目前正在執行的作業系統。

> [!TIP]
>  如果看不到您的內建屬性頁 （請參閱先前的附註），來執行 dll RegSvr32.exe 命令列使用的完整路徑名稱註冊的 DLL。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：新增關於內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)
