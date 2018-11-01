---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: cf4cea35386d1f781d6d2946c1730ba2e18dacea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624034"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Microsoft 專屬**

呼叫**Release**成員函式`IUnknown`上封裝的介面指標。

## <a name="syntax"></a>語法

```
void Release( );
```

## <a name="remarks"></a>備註

呼叫`IUnknown::Release`封裝的介面指標，引發`E_POINTER`錯誤，如果此介面的指標為 NULL。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)