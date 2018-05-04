---
title: 選項，ATL 控制項精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab1062d32aadc2ec4af68cda8bca02ac1a45a526
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="options-atl-control-wizard"></a>選項, ATL 控制項精靈
在這裡插入摘要的 「 搜尋結果 」。  
  
 使用精靈的這個頁面來定義您要建立的控制項的型別和它所包含的介面支援的層級。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **控制項類型**  
 您要建立的控制項類型。  
  
-   **標準控制項： ActiveX 控制項。**  
  
-   **複合控制項**: ActiveX 控制項可以包含 （類似於對話方塊中） 的其他 ActiveX 控制項或 Windows 控制項。 複合控制項，包括下列各項：  
  
    -   實作複合控制項的對話方塊範本。  
  
    -   自訂資源中，登錄中，會自動註冊時叫用的複合控制項。  
  
    -   C + + 類別，實作複合控制項。  
  
    -   複合控制項公開 COM 介面。  
  
    -   含有複合控制項的 HTML 測試網頁。  
  
     根據預設，此控制項設定[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)設定為 true，表示這是否為視窗型的控制項。 它會實作接收對應。 如需詳細資訊，請參閱[DHTML 控制項的支援](../../atl/atl-support-for-dhtml-controls.md)。  
  
-   **DHTML 控制項**: ATL DHTML 控制項，指定的使用者介面，使用 HTML。 DHTML UI 類別包含 COM 對應。 根據預設，此控制項設定[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)設定為 true，表示這是否為視窗型的控制項。  
  
     如需詳細資訊，請參閱[識別 DHTML 控制項專案的項目](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
 **最小控制項**  
 支援絕對多數容器所需的介面。 您可以設定**最小控制項**控制項類型的任何： 您可以建立最小的標準控制項、 最小的複合控制項或最小的 DHTML 控制項。  
  
 **彙總**  
 加入的控制項，您所建立的彙總支援。 如需詳細資訊，請參閱[彙總](../../atl/aggregation.md)。  
  
-   **[是]**： 建立可彙總的控制項。  
  
-   **否**： 建立不能彙總的控制項。  
  
-   **只有**： 建立只透過彙總具現化的控制項。  
  
 **執行緒模型**  
 指定控制項所使用的執行緒模型。  
  
-   **單一**： 控制項只在主要 COM 執行緒中執行。  
  
-   **Apartment**： 可以在任何單一執行緒 apartment 中建立控制項。 預設值。  
  
 **Interface**  
 這個控制項的容器所公開的介面的型別。  
  
-   **雙重**： 建立一個介面，公開屬性和方法，透過`IDispatch`和直接透過 VTBL。  
  
-   **自訂**： 建立公開直接透過 VTBL 方法的介面。  
  
     如果您選取**自訂**，接著，您可以指定控制項是**Automation 相容**。 如果您選取**Automation 相容**，則精靈會新增[oleautomation](../../windows/oleautomation.md) IDL 中的介面屬性和介面可以封送處理中 oleaut32.dll 通用封送處理器。 請參閱[封送處理的詳細資料](http://msdn.microsoft.com/library/windows/desktop/ms692621)如需詳細資訊的 Windows SDK 中。  
  
     此外，如果您選取**Automation 相容**，則在控制項中的所有方法的所有參數必須都是**VARIANT**相容。  
  
 **支援**  
 設定控制項的其他支援。  
  
-   **連接點**： 藉由衍生自物件的類別可讓您物件的連接點[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) ，並讓它的來源介面公開 （expose）。  
  
-   **授權**： 將支援的控制項加入[授權](http://msdn.microsoft.com/library/windows/desktop/ms690543)。 如果用戶端電腦具有正確的授權，就只能裝載授權的控制項。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)

