---
title: 實作雙重介面 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: ecd6a0cc90ca4175c4ae898f2e9aa8bf00508a3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262225"
---
# <a name="implementing-a-dual-interface"></a>實作雙重介面

您可以實作雙重介面，使用[IDispatchImpl](../atl/reference/idispatchimpl-class.md)類別，可提供的預設實作`IDispatch`雙重介面中的方法。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

若要使用此類別：

- 類型程式庫中定義您的雙重介面。

- 衍生類別的特製化從`IDispatchImpl`（傳遞資訊相關的介面和型別程式庫做為範本引數）。

- 將項目 （或項目） 新增至公開雙重介面 COM 對應`QueryInterface`。

- 在類別中實作之介面的 vtable 部分。

- 請確定在執行階段包含介面定義的型別程式庫是可為您的物件。

## <a name="atl-simple-object-wizard"></a>ATL 簡單物件精靈

如果您想要建立新的介面和新的類別，來實作它，您可以使用[ATL 加入類別對話方塊](../ide/add-class-dialog-box.md)，然後[ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)。

## <a name="implement-interface-wizard"></a>實作介面精靈

如果您有現有的介面，您可以使用[實作介面精靈](../atl/reference/adding-a-new-interface-in-an-atl-project.md)將必要的基底類別、 COM 對應項目和基本架構的方法實作新增至現有的類別。

> [!NOTE]
>  您可能需要調整所產生的基底類別，以便做為範本引數傳遞的類型程式庫的主要和次要的版本號碼您`IDispatchImpl`基底類別。 實作介面精靈並不會為您檢查的型別程式庫版本號碼。

## <a name="implementing-idispatch"></a>實作 IDispatch

您可以使用`IDispatchImpl`基底類別，以提供實作分配介面由 COM 對應中指定適當的項目 (使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)巨集)，只要您有描述相對應的雙重介面的型別程式庫。 它是相當常見實作`IDispatch`介面如此一來，例如。 ATL 簡單物件精靈] 及 [實作介面精靈同時假設您想要實作`IDispatch`如此一來，因此它們會將適當的項目加入對應。

> [!NOTE]
>  提供 ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md)並[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)類別可以幫助您實作分配介面，而不需要的類型程式庫，其中包含相容的雙重介面的定義。

## <a name="see-also"></a>另請參閱

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)
