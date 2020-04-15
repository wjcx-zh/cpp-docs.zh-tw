---
title: 參考計數 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321734"
---
# <a name="reference-counting"></a>參考計數

當 COM 本身認為物件不再被使用時,不會自動嘗試從記憶體中刪除該物件。 相反,物件程式員必須刪除未使用的物件。 程式員根據引用計數確定是否可以刪除物件。

COM`IUnknown`使用[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)的方法來管理物件上介面的引用計數。 呼叫這些方法的一般規則是:

- 每當用戶端收到介面指標時,`AddRef`都必須在介面上調用。

- 每當用戶端完成使用介面指標時,它必須呼叫`Release`。

在簡單實現中,每個`AddRef`調用都會`Release`遞減物件內的計數器變數。 當計數返回零時,介面不再具有任何用戶,並且可以自由地從記憶體中刪除自身。

還可以實現引用計數,以便計算對物件的每個引用(而不是單個介面)。 在這種情況下,每個`AddRef`物件調`Release`用 委託到物件的中央實現`Release`,並在 物件的引用計數達到零時釋放整個物件。

> [!NOTE]
> 使用新`CComObject`運算元構造派生物件時,引用**new**計數為 0。 因此,在成功創建`AddRef``CComObject`派生物件後,必須呼叫 。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[透過參考計數管理物件存留期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
