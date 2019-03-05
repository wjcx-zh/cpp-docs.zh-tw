---
title: CComEnum 類別
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 4d83b06f37c132c0d2325304e2cc155ccb490690
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290361"
---
# <a name="ccomenum-class"></a>CComEnum 類別

這個類別會定義 COM 列舉值物件的陣列為基礎。

## <a name="syntax"></a>語法

```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
T,
    Copy>,
public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>參數

*基底*<br/>
COM 列舉值介面。 請參閱[IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring)的範例。

*piid*<br/>
指標的列舉值介面的介面 ID。

*T*<br/>
列舉值介面所公開的項目類型。

*複製*<br/>
同質[複製原則類別](../../atl/atl-copy-policy-classes.md)。

*ThreadModel*<br/>
類別的執行緒模型。 此參數預設為您的專案中使用的全域物件執行緒模型。

## <a name="remarks"></a>備註

`CComEnum` 定義陣列為基礎的 COM 列舉值物件。 這個類別是類似[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)實作 c + + 標準程式庫容器為基礎的列舉值。 使用這個類別的一般步驟說明如下。 如需詳細資訊，請參閱 < [ATL 集合和列舉程式](../../atl/atl-collections-and-enumerators.md)。

## <a name="to-use-this-class"></a>若要使用此類別：

- **typedef**此類別的特製化。

- 使用**typedef**作為範本引數中的特製化`CComObject`。

- 建立的執行個體`CComObject`特製化。

- 初始化列舉值物件，藉由呼叫[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)。

- 傳回用戶端的列舉值介面。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

## <a name="example"></a>範例

如下所示的程式碼提供可重複使用的函式，用於建立和初始化的列舉值物件。

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

這個範本函式可以用來實作`_NewEnum`屬性的集合介面，如下所示：

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

此程式碼會建立**typedef** for`CComEnum`公開的變體透過向量`IEnumVariant`介面。 `CVariantArrayCollection`類別只會指定`CreateEnumerator`才能使用此型別，並傳遞必要的引數的列舉值物件。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl 類別](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)
