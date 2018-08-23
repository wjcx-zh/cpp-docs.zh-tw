---
title: Module::ReleaseNotifier::ReleaseNotifier 建構函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4ab2d5d03516147acda38ea2133d7445695de80
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598784"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier 建構函式

初始化的新執行個體**releasenotifier**類別。

## <a name="syntax"></a>語法

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>參數

*release*  
**真**若要刪除這個執行個體時`Release`方法稱為;**false**未刪除此執行個體。

## <a name="exceptions"></a>例外狀況

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Module::ReleaseNotifier 類別](../windows/module-releasenotifier-class.md)