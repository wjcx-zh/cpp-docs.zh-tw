---
title: CAtlFileMapping 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccbf3221bddf39c8069e20636c2f2a1deb597866
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116460"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 類別

此類別代表記憶體對應檔案，加入的方法中的轉換運算子[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>參數

*T*<br/>
用於轉換運算子的資料型別。

## <a name="members"></a>成員

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlFileMapping::operator T *](#operator_t_star)|允許隱含轉換`CAtlFileMapping`物件至`T*`。|

## <a name="remarks"></a>備註

此類別會加入單一的轉換運算子，以允許隱含轉換`CAtlFileMapping`物件至`T*`。 基底類別，提供其他成員[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>需求

**標頭：** atlfile.h

##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *

允許隱含轉換`CAtlFileMapping`物件至`T*`。

```
operator T*() const throw();
```

### <a name="return-value"></a>傳回值

傳回`T*`記憶體對應檔案開頭的指標。

### <a name="remarks"></a>備註

呼叫[CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata)並轉換為傳回的指標`T*`何處*T*是做為範本參數，這個類別的型別。

## <a name="see-also"></a>另請參閱

[CAtlFileMappingBase 類別](../../atl/reference/catlfilemappingbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
