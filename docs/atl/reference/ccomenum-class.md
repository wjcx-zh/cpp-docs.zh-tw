---
title: CComEnum 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17046239cf4ca5cc95afbc709f10b9c8aedaa9fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362859"
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
 `Base`  
 COM 列舉值 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 介面。  
  
 `piid`  
 列舉程式介面的介面 ID 的指標。  
  
 `T`  
 列舉程式介面所公開的項目類型。  
  
 `Copy`  
 同質[複製原則類別](../../atl/atl-copy-policy-classes.md)。  
  
 `ThreadModel`  
 類別的執行緒模型。 這個參數預設為使用您的專案中的全域物件執行緒模型。  
  
## <a name="remarks"></a>備註  
 `CComEnum` 定義 COM 列舉值物件的陣列為基礎。 這個類別是類似於[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)實作根據 c + + 標準程式庫容器的列舉值。 使用此類別的一般步驟如下所述。 如需詳細資訊，請參閱[ATL 集合和列舉程式](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="to-use-this-class"></a>若要使用此類別：  
  
- `typedef` 這個類別的特製化。  
  
-   使用`typedef`作為範本引數中的特製化`CComObject`。  
  
-   建立的執行個體`CComObject`特製化。  
  
-   藉由呼叫初始化列舉值物件[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)。  
  
-   傳回用戶端的列舉程式介面。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
## <a name="example"></a>範例  
 如下所示的程式碼可用於建立和初始化的列舉值物件的可重複使用函式。  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]  
  
 這個範本函式可以用來實作`_NewEnum`屬性的集合介面，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 此程式碼建立`typedef`如`CComEnum`可公開的向量**VARIANT**透過 s **IEnumVariant**介面。 **CVariantArrayCollection**類別只會指定**CreateEnumerator**才能使用這個型別和傳遞必要的引數的列舉值物件。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [CComEnumImpl 類別](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)
