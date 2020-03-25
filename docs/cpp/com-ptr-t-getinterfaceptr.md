---
title: _com_ptr_t::GetInterfacePtr
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetInterfacePtr
helpviewer_keywords:
- GetInterfacePtr method [C++]
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
ms.openlocfilehash: f3244d59159855ff4060c944874e859cb5ec23ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170731"
---
# <a name="_com_ptr_tgetinterfaceptr"></a>_com_ptr_t::GetInterfacePtr

**Microsoft 專屬**

傳回封裝的介面指標。

## <a name="syntax"></a>語法

```
Interface* GetInterfacePtr( ) const throw( );
Interface*& GetInterfacePtr() throw();
```

## <a name="remarks"></a>備註

傳回封裝的介面指標，可能為 NULL。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
