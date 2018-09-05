---
title: CInterfaceList 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9b0eb225f9da88db356fc4f04d25d2219876604
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752745"
---
# <a name="cinterfacelist-class"></a>CInterfaceList 類別

建構 COM 介面指標的清單時，這個類別會提供有用的方法。

## <a name="syntax"></a>語法

```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>參數

*I*  
COM 介面，用來指定要儲存的指標的類型。

*piid*  
指向 IID*我*。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CInterfaceList::CInterfaceList](#cinterfacelist)|介面清單建構函式。|

## <a name="remarks"></a>備註

這個類別會提供建構函式和衍生的方法，來建立 COM 介面指標的清單。 使用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)何時需要陣列。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList

介面清單建構函式。

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*  
區塊的大小，預設值是 10。

### <a name="remarks"></a>備註

區塊大小是記憶體的配置新的項目時所需數量的量值。 較大的區塊大小會減少記憶體配置常式，呼叫，但使用較多資源。

## <a name="see-also"></a>另請參閱

[CAtlList 類別](../../atl/reference/catllist-class.md)   
[CComQIPtr 類別](../../atl/reference/ccomqiptr-class.md)   
[CComQIPtrElementTraits 類別](../../atl/reference/ccomqiptrelementtraits-class.md)   
[類別概觀](../../atl/atl-class-overview.md)
