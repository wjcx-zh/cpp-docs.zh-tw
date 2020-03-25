---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 51182b461aeac83c12bb18a573a49b2d4347a190
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189921"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Microsoft 專屬**

在封裝的介面指標上呼叫 `IUnknown` 的 `AddRef` 成員函式。

## <a name="syntax"></a>語法

```
void AddRef( );
```

## <a name="remarks"></a>備註

在封裝的介面指標上呼叫 `IUnknown::AddRef`，如果指標是 Null，則引發 `E_POINTER` 錯誤。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
