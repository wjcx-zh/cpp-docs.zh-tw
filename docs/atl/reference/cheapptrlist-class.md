---
title: CHeapPtrList 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0e44475d7d9eee547e0e9d47c8d49c439d91bd1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766616"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList 類別

建構一份堆積指標時，這個類別會提供有用的方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>參數

*E*  
要儲存在集合類別的物件類型。

*配置器*  
要使用的記憶體配置類別。 預設值是[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|建構函式。|

## <a name="remarks"></a>備註

這個類別提供建構函式，並衍生方法從[CAtlList](../../atl/reference/catllist-class.md)並[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)協助儲存堆積指標集合類別物件的建立。

## <a name="inheritance-hierarchy"></a>繼承階層

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList

建構函式。

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*  
區塊大小。

### <a name="remarks"></a>備註

區塊大小是記憶體的配置新的項目時所需數量的量值。 較大的區塊大小會減少記憶體配置常式，呼叫，但使用較多資源。

## <a name="see-also"></a>另請參閱

[CAtlList 類別](../../atl/reference/catllist-class.md)   
[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)   
[CHeapPtrElementTraits 類別](../../atl/reference/cheapptrelementtraits-class.md)   
[類別概觀](../../atl/atl-class-overview.md)
