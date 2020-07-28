---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: cb5950e311711dd489b3cab223714b1840773f60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220583"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft 特定的**

封裝這個智慧型指標類型的一般介面指標。

## <a name="syntax"></a>語法

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>參數

*pInterface*<br/>
原始的介面指標。

*fAddRef*<br/>
如果是 **`true`** ，則 `AddRef` 會呼叫。 如果是 **`false`** ，物件會 `_com_ptr_t` 取得原始介面指標的擁有權，而不需要呼叫 `AddRef` 。

## <a name="remarks"></a>備註

- **Attach （**  *pInterface*  **）** `AddRef`不會呼叫。 介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。 `Release`呼叫以遞減先前封裝之指標的參考計數。

- **Attach （**  *pInterface* **，**  *fAddRef*  **）** 如果*fAddRef*為 **`true`** ， `AddRef` 則會呼叫來遞增封裝之介面指標的參考計數。 如果*fAddRef*為 **`false`** ，此 `_com_ptr_t` 物件會取得原始介面指標的擁有權，而不會呼叫 `AddRef` 。 `Release`呼叫以遞減先前封裝之指標的參考計數。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
