---
title: 'Handlet:: Handlet 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT, constructor
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4a932428b274f8ef8fcda88cd48a4d24464e818c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597212"
---
# <a name="handlethandlet-constructor"></a>HandleT::HandleT 建構函式

初始化的新執行個體**HandleT**類別。

## <a name="syntax"></a>語法

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()  
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>參數

*h*  
控制代碼。

## <a name="remarks"></a>備註

第一個建構函式初始化**HandleT**不是有效的控制代碼到物件的物件。 第二個建構函式會建立新**HandleT**從參數物件*h*。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HandleT 類別](../windows/handlet-class.md)