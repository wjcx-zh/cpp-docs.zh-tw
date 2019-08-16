---
title: CComEnumOnSTL 類別
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: ab11ea5e5347c9c8684e8710e9742fdbcad8a46b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497159"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL 類別

此類別會定義以C++標準程式庫集合為基礎的 COM 列舉值物件。

## <a name="syntax"></a>語法

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
T,
    Copy,
CollType>,
    public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>參數

*群體*<br/>
COM 列舉值。 如需範例, 請參閱[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。

*piid*<br/>
列舉值介面的介面識別碼指標。

*T*<br/>
列舉值介面所公開的專案類型。

*[複製]*<br/>
[複製原則](../../atl/atl-copy-policy-classes.md)類別。

*CollType*<br/>
C++標準程式庫容器類別。

## <a name="remarks"></a>備註

`CComEnumOnSTL`定義以C++標準程式庫集合為基礎的 COM 列舉值物件。 這個類別可以單獨使用或搭配[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。 使用此類別的一般步驟如下所述。 如需詳細資訊, 請參閱[ATL 集合和枚舉](../../atl/atl-collections-and-enumerators.md)器。

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>若要搭配 ICollectionOnSTLImpl 使用此類別:

- **typedef**這個類別的特製化。

- 使用**typedef**作為特製化`ICollectionOnSTLImpl`中的最終樣板引數。

如需範例, 請參閱[ATL 集合和枚舉](../../atl/atl-collections-and-enumerators.md)器。

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>若要使用與 ICollectionOnSTLImpl 無關的此類別:

- **typedef**這個類別的特製化。

- 在特製化`CComObject`中使用 typedef 做為樣板引數。

- 建立特製`CComObject`化的實例。

- 藉由呼叫[IEnumOnSTLImpl:: Init](../../atl/reference/ienumonstlimpl-class.md#init)來初始化列舉值物件。

- 將列舉值介面傳回用戶端。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

## <a name="example"></a>範例

下面所示的程式碼提供泛型函式來處理列舉值物件的建立和初始化:

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

此範本函式可以用來`_NewEnum`實作用集合介面的屬性, 如下所示:

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

這段程式碼 `CComEnumOnSTL`會建立的 typedef, 它會`CComVariant`透過`IEnumVariant`介面來公開的向量。 類別只是專門`CreateSTLEnumerator`用來處理這個型別的列舉值物件。 `CVariantCollection`

## <a name="see-also"></a>另請參閱

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[ATLCollections 範例:示範 ICollectionOnSTLImpl、CComEnumOnSTL 和自訂複製原則類別](../../overview/visual-cpp-samples.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl 類別](../../atl/reference/ienumonstlimpl-class.md)
