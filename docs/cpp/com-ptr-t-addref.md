---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 7408b5c174f76673b56caffd56aaa87895bd08d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663355"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef

**Microsoft 專屬**

呼叫`AddRef`成員函式`IUnknown`上封裝的介面指標。

## <a name="syntax"></a>語法

```
void AddRef( );
```

## <a name="remarks"></a>備註

呼叫`IUnknown::AddRef`封裝的介面指標，引發`E_POINTER`指標為 NULL 時的錯誤。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)