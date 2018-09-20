---
title: 'Mutex:: mutex 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7436aeb470804bd47dcc647ff0fe9a13faaae95
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444277"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex 建構函式

初始化的新執行個體**Mutex**類別。

## <a name="syntax"></a>語法

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制代碼或右值參考控制代碼，來**Mutex**物件。

## <a name="remarks"></a>備註

第一個建構函式初始化**Mutex**從指定的控制代碼的物件。 第二個建構函式初始化**Mutex**從指定的控制代碼，然後 mutex 擁有權移至目前的物件**Mutex**物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Mutex 類別](../windows/mutex-class1.md)