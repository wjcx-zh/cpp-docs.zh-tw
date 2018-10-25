---
title: CRBMap 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b4bf9678f2382c124bcfef484d0becf687f530
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072703"
---
# <a name="crbmap-class"></a>CRBMap 類別

此類別代表一使用紅黑二進位樹狀目錄的對應結構。

## <a name="syntax"></a>語法

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>參數

*K*<br/>
索引鍵的項目類型。

*V*<br/>
值的項目型別。

*KTraits*<br/>
程式碼，用來複製或移動索引鍵的項目。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。

*VTraits*<br/>
若要複製或移動值的項目所使用的程式碼。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRBMap::CRBMap](#crbmap)|建構函式。|
|[CRBMap:: ~ CRBMap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|呼叫這個方法來查閱索引鍵或值中的`CRBMap`物件。|
|[CRBMap::RemoveKey](#removekey)|呼叫這個方法來移除項目從`CRBMap`指定索引鍵的物件。|
|[CRBMap::SetAt](#setat)|呼叫這個方法來插入對應中的項目配對。|

## <a name="remarks"></a>備註

`CRBMap` 支援任何指定的型別，在管理索引鍵的項目和其關聯的值的已排序的陣列的對應陣列。 每個索引鍵可以有只有一個相關聯的值。 項目 （包含索引鍵和值） 會儲存在二進位樹狀目錄結構，使用[CRBMap::SetAt](#setat)方法。 可以使用來移除項目[CRBMap::RemoveKey](#removekey)方法，這會刪除具有指定的索引鍵值的項目。

周遊樹狀結構可能.remove 方法，進行這類[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，並[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。

*KTraits*並*VTraits*參數會包含任何複製或移動的項目所需的補充程式碼的 traits 類別。

`CRBMap` 衍生自[CRBTree](../../atl/reference/crbtree-class.md)，它會實作使用紅黑演算法二進位樹狀目錄。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)是一種變化，可讓每個索引鍵的多個值。 它也衍生自`CRBTree`，並因此共用許多功能與`CRBMap`。

兩者的替代方法`CRBMap`並`CRBMultiMap`提供[CAtlMap](../../atl/reference/catlmap-class.md)類別。 當只有少數的項目都必須儲存時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。

不同的集合類別以及其功能和效能特性的更完整討論，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="crbmap"></a>  CRBMap::CRBMap

建構函式。

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

*NBlockSize*參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小會減少記憶體配置常式，呼叫，但使用較多資源。 預設會針對 10 個項目配置空間一次。

請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需所提供的其他方法的詳細資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMap:: ~ CRBMap

解構函式。

```
~CRBMap() throw();
```

### <a name="remarks"></a>備註

會釋放所有配置的資源。

請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需所提供的其他方法的詳細資訊。

##  <a name="lookup"></a>  CRBMap::Lookup

呼叫這個方法來查閱索引鍵或值中的`CRBMap`物件。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
指定識別的項目，是要查閱的索引鍵。

*值*<br/>
收到的查閱值的變數。

### <a name="return-value"></a>傳回值

第一種形式的方法會傳回 true，如果找到索引鍵為，否則為 false。 第二個和第三個表單傳回的指標[CPair](crbtree-class.md#cpair_class)。

### <a name="remarks"></a>備註

請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需所提供的其他方法的詳細資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

##  <a name="removekey"></a>  CRBMap::RemoveKey

呼叫這個方法來移除項目從`CRBMap`指定索引鍵的物件。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
您想要移除對應至項目配對的索引鍵。

### <a name="return-value"></a>傳回值

如果金鑰是找到並移除，失敗則為 false，則傳回 true。

### <a name="remarks"></a>備註

請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需所提供的其他方法的詳細資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

##  <a name="setat"></a>  CRBMap::SetAt

呼叫這個方法來插入對應中的項目配對。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>參數

*key*<br/>
若要加入的索引鍵值`CRBMap`物件。

*值*<br/>
要加入至值`CRBMap`物件。

### <a name="return-value"></a>傳回值

傳回的位置中的索引鍵/值項目組`CRBMap`物件。

### <a name="remarks"></a>備註

`SetAt` 如果找到相符的索引鍵，會取代現有的項目。 如果找不到索引鍵，則會建立新的索引鍵/值組。

請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需所提供的其他方法的詳細資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[CRBTree 類別](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 類別](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap 類別](../../atl/reference/crbmultimap-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
