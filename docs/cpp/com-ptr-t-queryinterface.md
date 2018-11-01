---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 42953c92e4cf31b5ccd02dd51811fc1fdeedbcaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543828"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface

**Microsoft 專屬**

呼叫**QueryInterface**成員函式`IUnknown`上封裝的介面指標。

## <a name="syntax"></a>語法

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>參數

*iid*<br/>
`IID` 介面指標。

*p*<br/>
原始介面指標。

## <a name="remarks"></a>備註

呼叫`IUnknown::QueryInterface`具有指定之封裝的介面指標`IID`，並傳回產生的原始介面指標，在*p*。 此常式會傳回指出成功或失敗的 HRESULT。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)