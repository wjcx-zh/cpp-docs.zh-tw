---
title: 'Ftmbase:: Createglobalinterfacetable 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable
dev_langs:
- C++
helpviewer_keywords:
- CreateGlobalInterfaceTable method
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c042b6bd17da3459f499f9eb1c9167343c2e2ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578769"
---
# <a name="ftmbasecreateglobalinterfacetable-method"></a>FtmBase::CreateGlobalInterfaceTable 方法

建立全域介面表 (GIT)。

## <a name="syntax"></a>語法

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>參數

*Git*  
這項作業完成時，全域介面表的指標。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> `IGlobalInterfaceTable` 中的主題**COM 介面**的子主題**COM 參考**MSDN Library 中的主題。

## <a name="requirements"></a>需求

**標頭：** ftm.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[FtmBase 類別](../windows/ftmbase-class.md)