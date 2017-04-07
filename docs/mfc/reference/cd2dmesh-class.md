---
title: "CD2DMesh 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
dev_langs:
- C++
helpviewer_keywords:
- CD2DMesh class
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
caps.latest.revision: 17
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 78461adeaa0671b146ccb48f4e9145cbdceeb8cf
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dmesh-class"></a>CD2DMesh 類別
ID2D1Mesh 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DMesh : public CD2DResource;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DMesh::CD2DMesh](#cd2dmesh)|建構 CD2DMesh 物件。|  
|[CD2DMesh:: ~ CD2DMesh](#_dtorcd2dmesh)|解構函式。 D2D 網格物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DMesh::Attach](#attach)|會附加至現有的資源物件的介面|  
|[CD2DMesh::Create](#create)|建立 CD2DMesh。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DMesh::Destroy](#destroy)|終結 CD2DMesh 物件。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DMesh::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DMesh::Get](#get)|傳回 ID2D1Mesh 介面|  
|[CD2DMesh::IsValid](#isvalid)|檢查資源的有效性 (覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DMesh::Open](#open)|開啟網狀結構母體擴展。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DMesh::operator ID2D1Mesh *](#operator_id2d1mesh_star)|傳回 ID2D1Mesh 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DMesh::m_pMesh](#m_pmesh)|ID2D1Mesh 指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DMesh`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dmesh"></a>CD2DMesh:: ~ CD2DMesh  
 解構函式。 D2D 網格物件終結時呼叫。  
  
```  
virtual ~CD2DMesh();
```  
  
##  <a name="attach"></a>CD2DMesh::Attach  
 會附加至現有的資源物件的介面  
  
```  
void Attach(ID2D1Mesh* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有的資源介面。 不能是 NULL  
  
##  <a name="cd2dmesh"></a>CD2DMesh::CD2DMesh  
 建構 CD2DMesh 物件。  
  
```  
CD2DMesh(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `bAutoDestroy`  
 指出由擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="create"></a>CD2DMesh::Create  
 建立 CD2DMesh。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>CD2DMesh::Destroy  
 終結 CD2DMesh 物件。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DMesh::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1Mesh* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源介面指標。  
  
##  <a name="get"></a>CD2DMesh::Get  
 傳回 ID2D1Mesh 介面  
  
```  
ID2D1Mesh* Get();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1Mesh 介面的指標。  
  
##  <a name="isvalid"></a>CD2DMesh::IsValid  
 檢查資源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源無效，則為 TRUE否則為 FALSE。  
  
##  <a name="m_pmesh"></a>CD2DMesh::m_pMesh  
 ID2D1Mesh 指標。  
  
```  
ID2D1Mesh* m_pMesh;  
```  
  
##  <a name="open"></a>CD2DMesh::Open  
 開啟網狀結構母體擴展。  
  
```  
ID2D1TessellationSink* Open();
```  
  
### <a name="return-value"></a>傳回值  
 用來填入網狀結構 ID2D1TessellationSink 指標。  
  
##  <a name="operator_id2d1mesh_star"></a>CD2DMesh::operator ID2D1Mesh *  
 傳回 ID2D1Mesh 介面  
  
```  
operator ID2D1Mesh*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1Mesh 介面的指標。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

