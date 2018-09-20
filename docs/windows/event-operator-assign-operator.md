---
title: 'Event:: operator = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 072d4af94e4889d49d9b4876daa27cb4801d60d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447007"
---
# <a name="eventoperator-operator"></a>Event::operator= 運算子

指派指定的**事件**參考目前**事件**執行個體。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
若要為右值參考**事件**執行個體。

## <a name="return-value"></a>傳回值

目前的指標**事件**執行個體。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Event 類別 (Windows 執行階段 C++ 範本庫)](../windows/event-class-windows-runtime-cpp-template-library.md)