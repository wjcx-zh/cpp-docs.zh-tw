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
ms.openlocfilehash: 8e528bed14f3f6f3b35270975833bdd17fd777db
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422645"
---
# <a name="hstringoperator-operator"></a>HString::Operator= 運算子

將另一個值移**HString**物件與目前**HString**物件。

## <a name="syntax"></a>語法

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>參數

*other*<br/>
將現有**HString**物件。

## <a name="remarks"></a>備註

現有的值*其他*物件會複製到目前**HString**物件，然後*其他*物件被終結。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HString 類別](../windows/hstring-class.md)