---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 870e3580ed23ce994d832f7c59b951680d725e41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180494"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft 專屬**

封裝這個智慧型指標類型的一般介面指標。

## <a name="syntax"></a>語法

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>參數

*pInterface*<br/>
原始的介面指標。

*fAddRef*<br/>
如果為 TRUE，則會呼叫 `AddRef`。 如果為 FALSE，`_com_ptr_t` 物件會取得原始介面指標的擁有權，而不會呼叫 `AddRef`。

## <a name="remarks"></a>備註

- 不會呼叫**Attach （** *pInterface* **）** `AddRef`。 介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。 呼叫 `Release` 以遞減先前封裝之指標的參考計數。

- **Attach （**  *pInterface* **，**  *fAddRef*  **）** 如果*fAddRef*為 TRUE，則會呼叫 `AddRef` 來遞增封裝之介面指標的參考計數。 如果*fAddRef*為 FALSE，這個 `_com_ptr_t` 物件會取得原始介面指標的擁有權，而不會呼叫 `AddRef`。 呼叫 `Release` 以遞減先前封裝之指標的參考計數。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
