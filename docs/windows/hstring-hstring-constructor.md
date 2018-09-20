---
title: 'Hstring:: Hstring 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59ec7c1635b825cc300e28e5c02e2a3864a6c123
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442249"
---
# <a name="hstringhstring-constructor"></a>HString::HString 建構函式

初始化的新執行個體**HString**類別。

## <a name="syntax"></a>語法

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

#### <a name="parameters"></a>參數

*hstr*<br/>
HSTRING 控制代碼。

*other*<br/>
將現有**HString**物件。

## <a name="remarks"></a>備註

第一個建構函式初始化新**HString**是空的物件。

第二個建構函式初始化新**HString**的現有值的物件*其他*參數，然後終結*其他*參數。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HString 類別](../windows/hstring-class.md)