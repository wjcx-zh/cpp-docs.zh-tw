---
title: 'Module:: module 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Module
dev_langs:
- C++
helpviewer_keywords:
- Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0459c729368dc182de955f85afda514b2ff5071
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591858"
---
# <a name="modulemodule-constructor"></a>Module::Module 建構函式

初始化的新執行個體**模組**類別。

## <a name="syntax"></a>語法

```cpp
Module();
```

## <a name="remarks"></a>備註

這個建構函式受到保護，而且無法使用呼叫**新**關鍵字。 相反地，呼叫[module:: getmodule 方法](../windows/module-getmodule-method.md)或是[module:: create 方法](../windows/module-create-method.md)。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱
[Module 類別](../windows/module-class.md)