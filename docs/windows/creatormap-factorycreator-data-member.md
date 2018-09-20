---
title: 'Creatormap:: Factorycreator 資料成員 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
dev_langs:
- C++
helpviewer_keywords:
- factoryCreator data member
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 12d4fdd415ab37c9af0b0b34651e7cd2f00cf31b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405277"
---
# <a name="creatormapfactorycreator-data-member"></a>CreatorMap::factoryCreator 資料成員

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>參數

*currentflags*<br/>
其中一個[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

*entry*<br/>
CreatorMap。

*iidClassFactory*<br/>
Class factory 介面識別碼。

*處理站*<br/>
作業完成時，class factory 的位址。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

建立指定 CreatorMap factory。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[CreatorMap 結構](../windows/creatormap-structure.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)