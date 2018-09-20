---
title: 'Hstring:: Attach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
dev_langs:
- C++
ms.assetid: 69451979-0014-4959-bc5c-1e4ab6fb28e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2f0a9116e9abe07628d2b205bd5249d9354d6f88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413909"
---
# <a name="hstringattach-method"></a>HString::Attach 方法

將指定**HString**物件與目前**HString**物件。

## <a name="syntax"></a>語法

```cpp
void Attach(
       HSTRING hstr
       ) throw()  
```

### <a name="parameters"></a>參數

*hstr*<br/>
將現有**HString**物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HString 類別](../windows/hstring-class.md)