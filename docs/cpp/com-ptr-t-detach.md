---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154957"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Microsoft 專屬**

擷取和傳回封裝的介面指標。

## <a name="syntax"></a>語法

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>備註

擷取和傳回封裝的介面指標，並接著清除封裝的指標儲存體，為 NULL。 這麼做會從封裝中移除介面指標。 它可以決定是否要呼叫`Release`上傳回的介面指標。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)