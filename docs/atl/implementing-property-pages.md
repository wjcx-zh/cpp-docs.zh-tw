---
title: 實作屬性頁 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f00e95aee0f3e16a979f4969a33b90746b4082ea
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062401"
---
# <a name="implementing-property-pages"></a>實作屬性頁

屬性頁是 COM 物件實作`IPropertyPage`或`IPropertyPage2`介面。 ATL 提供支援，以實作透過屬性頁[ATL 屬性頁精靈](../atl/reference/atl-property-page-wizard.md)中[加入類別對話方塊](../ide/add-class-dialog-box.md)。

若要建立使用 ATL 屬性頁：

- 建立或開啟 ATL 動態連結程式庫 (DLL) 的伺服器專案。

- 開啟[加入類別對話方塊](../ide/add-class-dialog-box.md)，然後選取**ATL 屬性頁**。

- 請確定您的屬性頁面 （因為它有使用者介面） 執行緒的 apartment。

- 設定標題、 描述 （文件字串），以及與您的頁面相關聯的說明檔。

- 將控制項加入至產生的對話方塊資源做為您的屬性頁面的使用者介面。

- 回應變更您的頁面使用者介面，以執行驗證、 更新頁面的網站，或更新與您的頁面相關聯的物件。 特別是，呼叫[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)當使用者進行變更的屬性頁。

- 選擇性地覆寫`IPropertyPageImpl`方法使用以下的指導方針。

   |IPropertyPageImpl 方法|當您想要覆寫...|注意|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|執行基本的例行性檢查傳遞至您的頁面和其所支援的介面的物件數目。|執行您自己的程式碼，然後再呼叫基底類別實作。 如果所設定的物件不符合您的預期，您應儘速失敗呼叫。|
   |[啟用](../atl/reference/ipropertypageimpl-class.md#activate)|初始化您的頁面使用者介面 （例如，從物件中設定 最新的屬性值的對話方塊控制項、 控制項動態建立，或執行其他的初始設定）。|呼叫基底類別實作，您的程式碼之前，因此基底類別有機會建立對話方塊視窗中，所有控制項，然後再加以更新。|
   |[適用於](../atl/reference/ipropertypageimpl-class.md#apply)|驗證的屬性設定，並更新的物件。|就不需要呼叫基底類別實作，因為它不會執行任何除了追蹤呼叫。|
   |[停用](../atl/reference/ipropertypageimpl-class.md#deactivate)|清除與視窗相關的項目。|基底類別實作會終結代表屬性頁的對話方塊。 如果您需要清除，再終結對話方塊中，您應該加入程式碼，然後再呼叫基底類別。|

範例屬性頁面上實作，請參閱[範例： 實作屬性頁](../atl/example-implementing-a-property-page.md)。

> [!NOTE]
> 如果您想要裝載 ActiveX 控制項屬性頁中，您必須變更您精靈產生的類別衍生。 取代**CDialogImpl\<CYourClass >** 具有**CAxDialogImpl\<CYourClass >** 的基底類別清單中。

## <a name="see-also"></a>另請參閱

[屬性頁](../atl/atl-com-property-pages.md)<br/>
[ATLPages 範例](../visual-cpp-samples.md)
