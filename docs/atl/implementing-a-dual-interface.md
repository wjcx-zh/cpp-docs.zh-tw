---
title: 實現雙介面 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: a85597adad045bee3edb5cc3ed63c72a22fa08fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319459"
---
# <a name="implementing-a-dual-interface"></a>實現雙介面

您可以使用[IDispatchImpl](../atl/reference/idispatchimpl-class.md)類實現雙介面,該類提供雙`IDispatch`介面中 方法的預設實現。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

要使用此類:

- 在類型庫中定義雙介面。

- 從`IDispatchImpl`(傳遞有關介面的資訊和類型庫作為範本參數) 派生類。

- 向 COM 映射添加條目(或條目)`QueryInterface`以透過公開雙介面。

- 在類中實現介面的可 v 可部分。

- 確保包含介面定義的類型庫在運行時對物件可用。

## <a name="atl-simple-object-wizard"></a>ATL 簡單物件精靈

如果要建立新介面和新類別來實現它,可以使用[ATL 添加類別對話框](../ide/add-class-dialog-box.md),然後使用[ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)。

## <a name="implement-interface-wizard"></a>實作介面精靈

如果您有現有介面,則可以使用[實現介面嚮導](../atl/reference/adding-a-new-interface-in-an-atl-project.md)將必要的基類、COM 映射條目和骨架方法實現添加到現有類。

> [!NOTE]
> 您可能需要調整生成的基類,以便類型庫的主要版本號和次要版本號作為範本參數傳遞給`IDispatchImpl`基類。 實現介面嚮導不檢查類型庫版本號。

## <a name="implementing-idispatch"></a>實作 IDispatch

只要具有描述相應`IDispatchImpl`雙介面的類型庫,就可以使用基類通過在 COM 映射中指定適當的條目(使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)宏)來提供不相關介面的實現。 例如,`IDispatch`以這種方式實現介面很常見。 ATL 簡單物件嚮導和實現介面嚮導都假定您打算以這種方式`IDispatch`實現 ,因此它們將添加適當的條目到地圖中。

> [!NOTE]
> ATL 提供[IDispEventImpl](../atl/reference/idispeventimpl-class.md)和[IDispEventSimple](../atl/reference/idispeventsimpleimpl-class.md)類,可説明您實現解介面,而無需包含相容雙介面定義的類型庫。

## <a name="see-also"></a>另請參閱

[雙介面與 ATL](../atl/dual-interfaces-and-atl.md)
