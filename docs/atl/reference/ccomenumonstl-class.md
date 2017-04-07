---
title: "CComEnumOnSTL 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 23e234f82ce8c77a6ebde50070475deeab59f362
ms.lasthandoff: 02/24/2017

---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL 類別
這個類別會定義 c + + 標準程式庫集合為基礎的 COM 列舉值物件。  
  
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
 `Base`  
 COM 列舉值 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 介面。  
  
 `piid`  
 列舉程式介面的介面 ID 的指標。  
  
 `T`  
 列舉程式介面所公開的項目類型。  
  
 `Copy`  
 A[複製原則](../../atl/atl-copy-policy-classes.md)類別。  
  
 `CollType`  
 C + + 標準程式庫容器類別。  
  
## <a name="remarks"></a>備註  
 `CComEnumOnSTL`定義 c + + 標準程式庫集合為基礎的 COM 列舉值物件。 這個類別也可用在它自己或搭配[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。 使用這個類別的一般步驟說明如下。 如需詳細資訊，請參閱[ATL 集合和列舉程式](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>若要使用 ICollectionOnSTLImpl 這個類別︰  
  
- `typedef`這個類別的特製化。  
  
-   使用`typedef`的特製化中的最後一個範本引數為`ICollectionOnSTLImpl`。  
  
 請參閱[ATL 集合和列舉程式](../../atl/atl-collections-and-enumerators.md)範例。  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>若要使用這個類別與 ICollectionOnSTLImpl 分開︰  
  
- `typedef`這個類別的特製化。  
  
-   使用`typedef`中的特製化樣板引數為`CComObject`。  
  
-   建立的執行個體`CComObject`特製化。  
  
-   藉由呼叫初始化列舉值物件[IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init)。  
  
-   傳回列舉值介面給用戶端。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
## <a name="example"></a>範例  
 如下所示的程式碼提供處理建立和初始化的列舉值物件的泛型函式︰  
  
 [!code-cpp[NVC_ATL_COM&#34;](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 這個範本函式可以用來實作`_NewEnum`屬性的集合介面，如下所示︰  
  
 [!code-cpp[#35 NVC_ATL_COM](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 此程式碼會建立`typedef`的`CComEnumOnSTL`公開的向量`CComVariant`s 藉由**IEnumVariant**介面。 **CVariantCollection**類別只會指定**CreateSTLEnumerator**才能使用這個型別的列舉值物件。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections 範例︰ 示範 ICollectionOnSTLImpl、 CComEnumOnSTL，以及自訂複製原則類別](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl 類別](../../atl/reference/ienumonstlimpl-class.md)

