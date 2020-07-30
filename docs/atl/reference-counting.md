---
title: 參考計數（ATL）
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: f90c818e58ae7ef6e4a0b771cb53ae5b185d1617
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224340"
---
# <a name="reference-counting"></a>參考計數

COM 本身不會在認為物件不再使用時，自動嘗試從記憶體中移除物件。 相反地，物件程式設計人員必須移除未使用的物件。 程式設計人員會根據參考計數來決定是否可以移除物件。

COM 會使用 `IUnknown` [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)方法來管理物件上介面的參考計數。 呼叫這些方法的一般規則如下：

- 每當用戶端收到介面指標時， `AddRef` 都必須在介面上呼叫。

- 每當用戶端使用完介面指標時，它就必須呼叫 `Release` 。

在簡單的執行中，每個 `AddRef` 呼叫都會遞增，而每個 `Release` 呼叫都會遞減物件內的 counter 變數。 當計數傳回零時，介面就不再有任何使用者，而且可以自由地從記憶體移除。

參考計數也可以實作為計算物件的每個參考（而不是個別介面）。 在此情況下，每個 `AddRef` 和 `Release` 呼叫都會委派給物件上的中央執行，並 `Release` 在其參考計數到達零時釋放整個物件。

> [!NOTE]
> `CComObject`使用運算子來構造衍生物件時 **`new`** ，參考計數為0。 因此，在 `AddRef` 成功建立衍生物件之後，必須進行呼叫 `CComObject` 。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[透過參考計數管理物件存留期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
