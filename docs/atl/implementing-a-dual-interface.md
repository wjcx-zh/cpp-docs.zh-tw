---
title: " (ATL) 執行雙重介面"
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: 97d8cd912c85a74f3550a9ca6c7b87a9717d4075
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499548"
---
# <a name="implementing-a-dual-interface"></a>執行雙重介面

您可以使用 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 類別來執行雙重介面，以 `IDispatch` 在雙重介面中提供方法的預設執行。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

若要使用此類別：

- 在類型程式庫中定義您的雙重介面。

- 從 `IDispatchImpl` (將介面和類型程式庫的相關資訊傳遞給) 的範本引數，以衍生您的類別。

- 將專案 (或) 的專案加入至 COM 對應，以透過公開雙重介面 `QueryInterface` 。

- 在您的類別中執行介面的 vtable 部分。

- 確定您的物件在執行時間可以使用包含介面定義的類型程式庫。

## <a name="atl-simple-object-wizard"></a>ATL 簡單物件精靈

如果您想要建立新的介面和新的類別來執行它，可以使用 [ [Atl 加入類別] 對話方塊](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)，然後選擇 [ [Atl Simple Object Wizard]](../atl/reference/atl-simple-object-wizard.md)。

## <a name="implement-interface-wizard"></a>實作介面精靈

如果您有現有的介面，您可以使用 [ [執行介面] 嚮導](../atl/reference/adding-a-new-interface-in-an-atl-project.md) ，將必要的基類、COM 對應專案和基本架構方法的程式，加入至現有的類別。

> [!NOTE]
> 您可能需要調整產生的基類，以便將類型程式庫的主要和次要版本號碼當作範本引數傳遞至您的 `IDispatchImpl` 基類。 「執行介面嚮導」不會為您檢查類型程式庫版本號碼。

## <a name="implementing-idispatch"></a>實施 IDispatch

`IDispatchImpl`只要您有一個描述對應的雙重介面的類型程式庫，您就可以使用基類，藉由在 COM 對應中指定適當的專案，來提供產生器的實 (使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)宏) 。 `IDispatch`例如，以這種方式來執行介面相當常見。 ATL 簡單物件的 Wizard 和實介面 Wizard 都假設您想要以 `IDispatch` 這種方式執行，因此它們會將適當的專案加入至對應。

> [!NOTE]
> ATL 提供 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 和 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 類別，可協助您在不需要包含相容雙重介面定義的類型程式庫的情況下，執行介面。

## <a name="see-also"></a>另請參閱

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)
