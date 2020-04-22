---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 057d784bb495aefaeec1b86697a7421f6464cbd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745065"
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

*p 介面*<br/>
原始的介面指標。

*fAddRef*<br/>
如果為 TRUE,`AddRef`則調用。 如果是 FALSE,`_com_ptr_t`則 物件將取得原始介面指標的擁有權,而不`AddRef`呼叫 。

## <a name="remarks"></a>備註

- **不調用附加(p***介面***)。** `AddRef`     介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。 `Release`調用 以遞減以前封裝的指標的引用計數。

- **附加***(pInterface,fAddRef)* **,** *fAddRef* **)** 如果*fAddRef*為`AddRef`TRUE,則調用該值是為了增加封裝介面指標的引用計數。       如果*fAddRef*是`_com_ptr_t`FALSE,則此物件將取得原始`AddRef`介面指標 的擁有權,而不呼叫 。 `Release`調用 以遞減以前封裝的指標的引用計數。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t類](../cpp/com-ptr-t-class.md)
