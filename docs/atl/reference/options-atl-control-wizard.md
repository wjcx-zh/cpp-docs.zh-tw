---
title: 選項，ATL 控制項精靈 |Microsoft Docs
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
ms.openlocfilehash: 25116b0750016fdbb4ffd792d0b16efb6c6c1793
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711935"
---
# <a name="options-atl-control-wizard"></a>選項, ATL 控制項精靈

在這裡插入 [搜尋結果] 摘要。

您可以使用精靈的這個頁面來定義您要建立的控制項型別和它所包含的介面支援的層級。

## <a name="uielement-list"></a>UIElement 清單

### <a name="control-type"></a>控制項類型

您想要建立的控制項種類。

- **標準控制項**: ActiveX 控制項。

- **複合控制項**: ActiveX 控制項，它可以包含 （類似於對話方塊中） 其他 ActiveX 控制項或 Windows 控制項。 複合控制項包含下列項目：

   - 實作複合控制項的對話方塊範本。

   - 自訂資源中，登錄，這樣會自動註冊時叫用的複合控制項。

   - C + + 類別實作複合控制項。

   - 複合控制項所公開 COM 介面。

   - 含有複合控制項的 HTML 測試網頁。

     根據預設，設定這個控制項[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)為 true，表示視窗化控制項。 它會實作接收對應。 如需詳細資訊，請參閱 < [DHTML 控制項的支援](../../atl/atl-support-for-dhtml-controls.md)。

- **DHTML 控制項**: ATL DHTML 控制項指定的使用者介面，使用 HTML。 DHTML UI 類別包含 COM 對應。 根據預設，設定這個控制項[CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly)為 true，表示視窗化控制項。

     如需詳細資訊，請參閱 <<c0> [ 識別 DHTML 控制項專案的項目](../../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

### <a name="minimal-control"></a>最小的控制項

支援絕對所需的大部分容器的介面。 您可以設定**最小控制項**任何控制項類型： 您可以建立最小的標準控制項、 最小的複合控制項或最小的 DHTML 控制項。

### <a name="aggregation"></a>彙總

新增彙總支援您所建立的控制項。 如需詳細資訊，請參閱 <<c0> [ 彙總](../../atl/aggregation.md)。

- **是**： 建立可彙總的控制項。

- **否**： 建立無法彙總的控制項。

- **只有**： 建立只能透過彙總具現化的控制項。

### <a name="threading-model"></a>執行緒模型

指定控制項所使用的執行緒模型。

- **單一**： 控制項只在主要 COM 執行緒中執行。

- **Apartment**： 可以在任何單一執行緒 apartment 中建立控制項。 預設值。

### <a name="interface"></a>介面

這個控制項的容器所公開的介面的型別。

- **雙重**： 建立公開屬性和方法，透過介面`IDispatch`和直接透過 VTBL。

- **自訂**： 建立公開 VTBL 透過直接方法的介面。

   如果您選取**自訂**，則您可以指定控制項是**自動化相容**。 如果您選取**自動化相容**，然後精靈會新增[oleautomation](../../windows/oleautomation.md)屬性在介面中的 IDL 和介面可以封送處理由 oleaut32.dll 中通用封送處理器。 請參閱[封送處理的詳細資料](/windows/desktop/com/marshaling-details)Windows sdk for 的詳細資訊。

   此外，如果您選取**自動化相容**，則控制項中的所有方法的所有參數必須都是 VARIANT 相容。

### <a name="support"></a>支援

設定控制項的其他支援。

- **連接點**： 藉由衍生自物件的類別讓您為物件的連接點[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)並讓它公開 （expose） 的來源介面。

- **授權**： 將支援新增至的控制項[授權](/windows/desktop/com/licensing)。 如果用戶端電腦具有正確的授權，就只能裝載授權的控制項。

## <a name="see-also"></a>另請參閱

[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)

