---
title: 'Hstring:: Operator = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9294650db7a1b18c2542603988952a80b3f1905d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598541"
---
# <a name="hstringoperator-operator"></a>HString::Operator= 運算子

將另一個值移**HString**物件與目前**HString**物件。

## <a name="syntax"></a>語法

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>參數

*other*  
將現有**HString**物件。

## <a name="remarks"></a>備註

現有的值*其他*物件會複製到目前**HString**物件，然後*其他*物件被終結。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HString 類別](../windows/hstring-class.md)