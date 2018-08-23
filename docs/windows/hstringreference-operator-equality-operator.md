---
title: 'Hstringreference:: Operator = = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs:
- C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b07df3dc50704a87883e1a387fe9c842c1732b54
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610529"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator== 運算子

指出兩個參數是否相等。

## <a name="syntax"></a>語法

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
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