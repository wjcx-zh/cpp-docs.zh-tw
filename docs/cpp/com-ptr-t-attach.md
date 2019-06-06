---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 4b4b7a21d12cc645c486dd93d555510c1e716563
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154886"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach

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
如果它是 TRUE，則`AddRef`呼叫。 如果是 FALSE 時，`_com_ptr_t`物件會取得擁有權的一般介面指標，而不需呼叫`AddRef`。

## <a name="remarks"></a>備註

- **附加 (** *pInterface* **)** `AddRef`就不會呼叫。 介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。 `Release` 呼叫以遞減先前封裝之指標的參考計數。

- **附加 (** *pInterface* **，** *fAddRef* **)** 如果*fAddRef*為 TRUE， `AddRef`呼叫以遞增封裝的介面指標的參考計數。 如果*fAddRef*為 FALSE，這`_com_ptr_t`物件會取得擁有權的一般介面指標，而不需呼叫`AddRef`。 `Release` 呼叫以遞減先前封裝之指標的參考計數。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)