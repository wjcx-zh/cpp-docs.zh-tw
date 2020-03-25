---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 26dda2dff83ff0adbb7ef05c5e75f64b44138bd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170667"
---
# <a name="_com_ptr_tqueryinterface"></a>_com_ptr_t::QueryInterface

**Microsoft 專屬**

在封裝的介面指標上呼叫 `IUnknown` 的**QueryInterface**成員函式。

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
介面指標的 `IID`。

*p*<br/>
原始介面指標。

## <a name="remarks"></a>備註

使用指定的 `IID` 在封裝的介面指標上呼叫 `IUnknown::QueryInterface`，並在*p*中傳回產生的原始介面指標。 此常式會傳回 HRESULT 以表示成功或失敗。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
