---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 4dcf643357c9b368d4b2ea3bc51e6567acf45a44
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745099"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Microsoft 特定的**

調用`AddRef`封裝介面指標`IUnknown`上的成員函數。

## <a name="syntax"></a>語法

```cpp
void AddRef( );
```

## <a name="remarks"></a>備註

呼叫`IUnknown::AddRef`封裝的介面指標,如果指標為`E_POINTER`NULL,則引發錯誤。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t類](../cpp/com-ptr-t-class.md)
