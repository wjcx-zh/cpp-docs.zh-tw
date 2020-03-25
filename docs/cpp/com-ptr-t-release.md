---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: f455e855e782a939e79898ee46e445f65d25d37a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170588"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Microsoft 專屬**

在封裝的介面指標上呼叫 `IUnknown` 的**Release**成員函式。

## <a name="syntax"></a>語法

```
void Release( );
```

## <a name="remarks"></a>備註

在封裝的介面指標上呼叫 `IUnknown::Release`，如果這個介面指標是 Null，則引發 `E_POINTER` 錯誤。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
