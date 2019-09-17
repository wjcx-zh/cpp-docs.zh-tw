---
title: CComEnum 類別
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 7252eb2fa5d34618a1c38484a2506bae27a1106a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497214"
---
# <a name="ccomenum-class"></a>CComEnum 類別

這個類別會定義以陣列為基礎的 COM 列舉值物件。

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

*群體*<br/>
COM 列舉值介面。 如需範例，請參閱[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。

*piid*<br/>
列舉值介面的介面識別碼指標。

*T*<br/>
列舉值介面所公開的專案類型。

*[複製]*<br/>
同質[複製原則類別](../../atl/atl-copy-policy-classes.md)。

*ThreadModel*<br/>
類別的執行緒模型。 這個參數預設為您專案中使用的全域物件執行緒模型。

## <a name="remarks"></a>備註

`CComEnum`定義以陣列為基礎的 COM 列舉值物件。 這個類別類似于根據 C++標準程式庫容器來執行列舉值的 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)。 使用此類別的一般步驟如下所述。 如需詳細資訊，請參閱[ATL 集合和枚舉](../../atl/atl-collections-and-enumerators.md)器。

## <a name="to-use-this-class"></a>若要使用此類別：

- **typedef**這個類別的特製化。

- 在特製化`CComObject`中使用 typedef 做為樣板引數。

- 建立特製`CComObject`化的實例。

- 藉由呼叫[CComEnumImpl：： Init](../../atl/reference/ccomenumimpl-class.md#init)來初始化列舉值物件。

- 將列舉值介面傳回用戶端。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

## <a name="example"></a>範例

下面所示的程式碼提供可重複使用的函式，以建立和初始化列舉值物件。

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

此範本函式可以用來`_NewEnum`實作用集合介面的屬性，如下所示：

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

這段`CComEnum`程式碼會建立的**typedef** ，它會透過`IEnumVariant`介面公開變數的向量。 類別只是專門`CreateEnumerator`用來處理這個型別的列舉值物件，並傳遞必要的引數。 `CVariantArrayCollection`

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl 類別](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)
