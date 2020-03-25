---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: 8ba42f19e3474cc4a3199771f761b021221f430e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190010"
---
# <a name="_com_ptr_tdetach"></a>_com_ptr_t::Detach

**Microsoft 專屬**

擷取和傳回封裝的介面指標。

## <a name="syntax"></a>語法

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>備註

擷取和傳回封裝的介面指標，然後將封裝的指標儲存區清除為 NULL。 這麼做會從封裝中移除介面指標。 您可以視需要在傳回的介面指標上呼叫 `Release`。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
