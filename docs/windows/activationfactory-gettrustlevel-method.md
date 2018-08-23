---
title: 'Activationfactory:: Gettrustlevel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bfec8bfa6940fd4a702334f0d3068c6d936ea8c1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607310"
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel 方法

取得物件的信任層級，目前**ActivationFactory**具現化。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>參數

*trustLvl*  
這項作業完成時，執行階段的信任層級類別**ActivationFactory**具現化。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，會發出判斷提示錯誤以及*trustLvl*設定為`FullTrust`。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ActivationFactory 類別](../windows/activationfactory-class.md)