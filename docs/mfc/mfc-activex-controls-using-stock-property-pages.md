---
title: MFC ActiveX 控制項： 使用內建屬性頁 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e8d54f87e4e018a004bbab503664fa1788f36c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347126"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控制項：使用內建屬性頁
這篇文章討論可用的 ActiveX 控制項，以及如何使用這些內建屬性頁。  
  
 如需在 ActiveX 控制項中使用屬性頁的詳細資訊，請參閱下列文章：  
  
-   [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC ActiveX 控制項：新增另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC ActiveX 控制項用於提供三個內建屬性頁： **CLSID_CColorPropPage**， **CLSID_CFontPropPage**，和**CLSID_CPicturePropPage**。 這些頁面會分別顯示內建的色彩、 字型和圖片屬性的使用者介面。  
  
 若要併入控制這些屬性頁，將其識別碼加入初始化控制項的屬性頁 Id 陣列的程式碼。 下列範例中，在這段程式碼，位於控制項實作檔 (。CPP) 初始化陣列，包含所有的三個內建屬性頁和 [預設] 屬性頁 (名為`CMyPropPage`在此範例中):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 請注意，在屬性的計數頁面`BEGIN_PROPPAGEIDS`巨集，為 4。 這表示 ActiveX 控制項所支援的屬性頁的數目。  
  
 在進行這些修改之後，重建您的專案。 控制項現在會有字型、 圖片和色彩屬性的屬性的頁。  
  
> [!NOTE]
>  如果無法存取控制項內建屬性頁，它可能是因為 MFC DLL (MFCxx.DLL) 尚未正確註冊與目前的作業系統。 這通常會產生不同於目前執行的作業系統安裝 Visual c + +。  
  
> [!TIP]
>  如果看不到內建屬性頁 （請參閱如上一個附註），從命令列的完整路徑名稱，執行 RegSvr32.exe，dll 註冊 DLL。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：新增內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)

