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
ms.openlocfilehash: 18e482ca93166246df7569be9babff93d983dfd5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618069"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控制項：使用內建屬性頁

本文討論 ActiveX 控制項可用的內建屬性頁，以及如何使用它們。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

如需在 ActiveX 控制項中使用屬性頁的詳細資訊，請參閱下列文章：

- [MFC ActiveX 控制項：屬性頁](mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控制項：加入另一個自訂屬性頁](mfc-activex-controls-adding-another-custom-property-page.md)

MFC 提供三個內建屬性頁來與 ActiveX 控制項搭配使用： `CLSID_CColorPropPage` 、 `CLSID_CFontPropPage` 和 `CLSID_CPicturePropPage` 。 這些頁面會分別顯示 [內建色彩]、[字型] 和 [圖片] 屬性的使用者介面。

若要將這些屬性頁併入控制項中，請將其 Id 新增至程式碼，以初始化控制項的屬性頁 Id 陣列。 在下列範例中，此程式碼位於控制項執行檔（。CPP），初始化陣列以包含三個內建屬性頁和預設屬性頁（ `CMyPropPage` 在此範例中命名為）：

[!code-cpp[NVC_MFC_AxOpt#21](codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

請注意，在 BEGIN_PROPPAGEIDS 宏的屬性頁計數為4。 這表示 ActiveX 控制項支援的屬性頁數目。

進行這些修改之後，請重建您的專案。 您的控制項現在具有 [字型]、[圖片] 和 [色彩] 屬性的屬性頁。

> [!NOTE]
> 如果無法存取 [控制項內建] 屬性頁，可能是因為 MFC DLL （MFCxx）並未正確地向目前的作業系統註冊。 這通常是因為在不同于目前執行的作業系統下安裝 Visual C++ 所造成。

> [!TIP]
> 如果看不到您的內建屬性頁（請參閱上一個附注），請從命令列執行 RegSvr32 .exe，並將完整路徑名稱加入 DLL，以註冊 DLL。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：新增內建屬性](mfc-activex-controls-adding-stock-properties.md)
