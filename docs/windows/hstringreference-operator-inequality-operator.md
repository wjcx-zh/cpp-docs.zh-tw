---
title: 'Hstringreference:: Operator ！ = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91ad2c531ffefa0ac832e63dffeaa2b292243cf6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596224"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!= 運算子

表示兩個參數是否不相等。

## <a name="syntax"></a>語法

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>參數

*lhs*  
要比較的第一個參數。 *lhs*可以是**HStringReference**物件或 HSTRING 控制代碼。

*rhs*  
要比較的第二個參數。  *rhs*可以是**HStringReference**物件或 HSTRING 控制代碼。

## <a name="return-value"></a>傳回值

**真**如果*lhs*並*rhs*參數不相等，否則**false**。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HStringReference 類別](../windows/hstringreference-class.md)