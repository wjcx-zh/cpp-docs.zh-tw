---
title: 選項, ATL 控制項精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 25db3995687011de5e9cc0a98506cd26f2f1af0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495446"
---
# <a name="options-atl-control-wizard"></a>選項, ATL 控制項精靈

使用嚮導的這個頁面, 即可定義您要建立的控制項類型, 以及它所包含的介面支援層級。

## <a name="uielement-list"></a>UIElement 清單

### <a name="control-type"></a>控制項類型

您想要建立的控制項類型。

- **標準控制項**:ActiveX 控制項。

- **複合控制項**:可以包含 (類似于對話方塊) 其他 ActiveX 控制項或 Windows 控制項的 ActiveX 控制項。 複合控制項包括下列各項:

  - 執行複合控制項之對話方塊的範本。

  - 自訂資源, 登錄, 它會在叫用時自動註冊複合控制項。

  - 實C++作為複合控制項的類別。

  - COM 介面, 由複合控制項公開。

  - 包含複合控制項的 HTML 測試頁。

    根據預設, 此控制項會將[CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)設為 true, 以指出這是視窗型控制項。 它會實行接收對應。 如需詳細資訊, 請參閱[DHTML 控制項的支援](../../atl/atl-support-for-dhtml-controls.md)。

- **DHTML 控制項**:ATL DHTML 控制項使用 HTML 來指定使用者介面。 DHTML UI 類別包含 COM 對應。 根據預設, 此控制項會將[CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)設為 true, 以指出這是視窗型控制項。

   如需詳細資訊, 請參閱[識別 DHTML 控制項專案的元素](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

### <a name="minimal-control"></a>最小控制

僅支援大部分容器絕對需要的介面。 您可以為任何控制項類型設定**最小的控制**: 您可以建立最小的標準控制項、最小的複合控制項, 或最小的 DHTML 控制項。

### <a name="aggregation"></a>彙總

加入您所建立之控制項的匯總支援。 如需詳細資訊, 請參閱[匯總](../../atl/aggregation.md)。

- **是**:建立可匯總的控制項。

- **否**:建立無法匯總的控制項。

- **僅限**:建立只能透過匯總具現化的控制項。

### <a name="threading-model"></a>執行緒模型

指定控制項所使用的執行緒模型。

- **單一**:控制項只會在主要 COM 執行緒中執行。

- **公寓**:控制項可以在任何單一執行緒的單元中建立。 預設值。

### <a name="interface"></a>介面

此控制項公開給容器的介面類別型。

- **雙重**:建立介面, 透過`IDispatch`和直接透過 VTBL 公開屬性和方法。

- **自訂**：建立介面, 透過 VTBL 直接公開方法。

   如果您選取 [**自訂**], 則可以指定控制項與**自動化相容**。 如果您選取 [**自動化相容**], 則 wizard 會將[oleautomation](../../windows/oleautomation.md)屬性加入至 IDL 中的介面, 而且介面可以由 oleaut32.lib 中的通用封送處理器封送處理。 如需詳細資訊, 請參閱 Windows SDK 中的[封送處理詳細資料](/windows/win32/com/marshaling-details)。

   此外, 如果您選取 [**自動化相容**], 則控制項中所有方法的所有參數都必須與變體相容。

### <a name="support"></a>支援

設定控制項的其他其他支援。

- **連接點**:藉由讓物件的類別衍生自[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) , 並允許它公開來源介面, 為您的物件啟用連接點。

- **授權**:將支援新增至控制項以進行[授權](/windows/win32/com/licensing)。 只有在用戶端電腦擁有正確的授權時, 才可以主控授權的控制項。

## <a name="see-also"></a>另請參閱

[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)
