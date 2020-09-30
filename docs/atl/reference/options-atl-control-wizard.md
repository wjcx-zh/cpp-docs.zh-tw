---
title: 選項, ATL 控制項精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 481c97fe7621e9592317f629c2cf87f2f719d5d1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506914"
---
# <a name="options-atl-control-wizard"></a>選項, ATL 控制項精靈

使用 wizard 的這個頁面，即可定義您正在建立的控制項類型，以及它所包含的介面支援層級。

## <a name="uielement-list"></a>UIElement 清單

### <a name="control-type"></a>控制項類型

您要建立的控制項類型。

- **標準控制項**： ActiveX 控制項。

- **複合控制項**： activex 控制項，它可以包含與對話方塊相同的 (，) 其他 ActiveX 控制項或 Windows 控制項。 複合控制項包含下列各項：

  - 執行複合控制項之對話方塊的範本。

  - 自訂資源：登錄，它會在叫用時自動註冊複合控制項。

  - 執行複合控制項的 c + + 類別。

  - 由複合控制項公開的 COM 介面。

  - 包含複合控制項的 HTML 測試頁面。

    根據預設，此控制項會將 [CComControlBase：： m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) 設定為 true，表示這是視窗控制項。 它會實行接收對應。 如需詳細資訊，請參閱 [支援 DHTML 控制項](../../atl/atl-support-for-dhtml-controls.md)。

- **DHTML 控制項**： ATL DHTML 控制項使用 HTML 指定使用者介面。 DHTML UI 類別包含 COM 對應。 根據預設，此控制項會將 [CComControlBase：： m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) 設定為 true，表示這是視窗控制項。

   如需詳細資訊，請參閱 [識別 DHTML 控制項專案的元素](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

### <a name="minimal-control"></a>基本控制

僅支援大部分容器絕對需要的介面。 您可以設定任何控制項類型的 **最基本控制** ：您可以建立最基本的標準控制項、最基本的複合控制項，或最基本的 DHTML 控制項。

### <a name="aggregation"></a>彙總

為您所建立的控制項新增匯總支援。 如需詳細資訊，請參閱 [匯總](../../atl/aggregation.md)。

- **是**：建立可匯總的控制項。

- **否**：建立無法匯總的控制項。

- **僅限**：建立只能透過匯總具現化的控制項。

### <a name="threading-model"></a>執行緒模型

指定控制項使用的執行緒模型。

- **Single**：控制項只會在主要 COM 執行緒中執行。

- **單元**：可以在任何單一線程單元中建立控制項。 預設值。

### <a name="interface"></a>介面

此控制項公開給容器的介面類別型。

- **雙重**：建立介面，直接透過 VTBL 公開屬性和方法 `IDispatch` 。

- **自訂**：建立介面，直接透過 VTBL 公開方法。

   如果您選取 [ **自訂**]，則可以指定控制項為 **自動化相容**。 如果您選取 [ **自動化相容**]，則嚮導會將 [oleautomation](../../windows/attributes/oleautomation.md) 屬性加入至 IDL 中的介面，而介面可由 oleaut32.dll 中的通用封送處理器封送處理。 如需詳細資訊，請參閱 Windows SDK 中的 [封送處理詳細資料](/windows/win32/com/marshaling-details) 。

   此外，如果您選取 [ **自動化相容**]，則控制項中所有方法的所有參數都必須具有 VARIANT 相容性。

### <a name="support"></a>支援

為控制項設定其他的其他支援。

- **連接點**：讓物件的類別衍生自 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 並允許它公開來源介面，藉以啟用物件的連接點。

- **授權**：新增對控制項的支援以供 [授權](/windows/win32/com/licensing)之用。 只有在用戶端電腦具有正確的授權時，才可以主控授權的控制項。

## <a name="see-also"></a>另請參閱

[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)
