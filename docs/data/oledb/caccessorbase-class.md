---
title: CAccessorBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
dev_langs:
- C++
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18199a700cbc5065d987a57cc076a5d0cf670577
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340660"
---
# <a name="caccessorbase-class"></a>CAccessorBase 類別
OLE DB 範本中的所有存取子會衍生自這個類別。 `CAccessorBase` 可讓管理多個存取子的一個資料列集。 它也會提供參數和輸出資料行的繫結。  
  
## <a name="syntax"></a>語法

```cpp
// Replace with syntax  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[關閉](#close)|關閉存取子。|  
|[GetHAccessor](#geth)|擷取存取子控制代碼。|  
|[GetNumAccessors](#getnum)|擷取此類別所建立的存取子數目。|  
|[IsAutoAccessor](#isauto)|測試指定的存取子是否 autoaccessor。|  
|[ReleaseAccessors](#release)|釋放存取子。|  

## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  

## <a name="close"></a> Caccessorbase:: Close
關閉存取子。  
  
### <a name="syntax"></a>語法  
  
```cpp
void Close();  
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)第一次。  

## <a name="geth"></a> Caccessorbase:: Gethaccessor
擷取指定之存取子的存取子控制代碼。  
  
### <a name="syntax"></a>語法  
  
```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>參數  
 *nAccessor*  
 [in] 存取子的零位移數字。  
  
### <a name="return-value"></a>傳回值  
 存取子控制代碼。  

## <a name="getnum"></a> Caccessorbase:: Getnumaccessors
擷取此類別所建立的存取子數目。  
  
### <a name="syntax"></a>語法  
  
```cpp
ULONG GetNumAccessors() const;  
```  
  
### <a name="return-value"></a>傳回值  
 類別所建立的存取子數目。  

## <a name="isauto"></a> Caccessorbase:: Isautoaccessor
如果會自動擷取資料的存取子的移動作業期間，則傳回 true。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool IsAutoAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>參數  
 *nAccessor*  
 [in] 存取子的零位移數字。  
  
### <a name="return-value"></a>傳回值  
 傳回 **，則為 true**如果存取子是 autoaccessor。 否則會傳回 **false**。  

## <a name="release"></a> Caccessorbase:: Releaseaccessors
釋放存取子類別建立的。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);  
```  
  
#### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標`IUnknown`已為其建立存取子的 COM 物件的介面。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT。  
  
### <a name="remarks"></a>備註  
 從呼叫[caccessorrowset:: Close](../../data/oledb/caccessorrowset-close.md)。 
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessorBase 類別](../../data/oledb/caccessorbase-class.md)