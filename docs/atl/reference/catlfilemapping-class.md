---
title: CAtlFileMapping 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: d0a47a6cf0cc86409ceb9ef40d6fc6d738c86aa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247165"
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

##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T*

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
