---
title: 多個雙重介面
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
ms.openlocfilehash: 2ed0e9e8c74e02917e852b8f95ebff1b048afaef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261575"
---
# <a name="multiple-dual-interfaces"></a>多個雙重介面

您可能想要合併的雙重介面的優點 (也就是彈性 vtable 和晚期繫結，因此讓類別可供指令碼語言也做為C++) 與技術在多重繼承。

雖然可以公開 （expose） 單一的 COM 物件上的多個雙重介面，但不建議。 如果有多個雙重介面，必須有只有一個`IDispatch`公開的介面。 可用以確保這種情況的技巧會執行例如失去函式或更高的程式碼複雜度的負面影響。 優點和缺點，應該仔細衡量考慮這種方法，開發人員。

## <a name="exposing-a-single-idispatch-interface"></a>公開單一的 IDispatch 介面

可以藉由衍生自兩個以上的特製化會公開單一物件上的多個雙重介面`IDispatchImpl`。 不過，如果您允許查詢的用戶端`IDispatch`介面，您必須使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)巨集 (或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) 來指定要用於哪一個基底類別實作`IDispatch`。

[!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]

因為只有一個`IDispatch`介面公開，只能存取您的物件，透過的用戶端`IDispatch`介面不能存取的方法或任何其他介面中的屬性。

## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>將多個雙重介面結合成單一實作 IDispatch

ATL 不提供任何支援的單一實作中結合多個雙重介面`IDispatch`。 不過，有數種已知的方法，以手動方式結合介面，例如建立樣板化類別，其中包含的個別等位`IDispatch`介面，建立新的物件來執行`QueryInterface`函式，或使用typeinfo 為基礎的巢狀的物件，以建立實作`IDispatch`介面。

這些方法會有潛在的命名空間衝突，以及程式碼複雜度與可維護性問題。 不建議您建立多個雙重介面。

## <a name="see-also"></a>另請參閱

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)
