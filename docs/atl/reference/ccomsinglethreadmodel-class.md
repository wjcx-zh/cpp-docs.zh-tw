---
title: CComSingleThreadModel 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: af19ac34e6a21aeb16278957b4e3df533a607d23
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883433"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 類別
這個類別提供方法遞增和遞減變數的值。  
  
## <a name="syntax"></a>語法  
  
```
class CComSingleThreadModel
```  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComSingleThreadModel::CriticalSection](#criticalsection)|參考類別`CComFakeCriticalSection`。|  
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|參考`CComSingleThreadModel`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComSingleThreadModel::Decrement](#decrement)|遞減指定變數的值。 此實作不具備執行緒安全。|  
|[CComSingleThreadModel::Increment](#increment)|遞增指定變數的值。 此實作不具備執行緒安全。|  
  
## <a name="remarks"></a>備註  
 `CComSingleThreadModel` 提供方法來遞增及遞減變數的值。 不同於[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)並[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這些方法並不具備執行緒安全。  

 一般而言，您可以使用`CComSingleThreadModel`透過其中兩個**typedef**名稱，或是[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或是[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。 每個參考的類別**typedef**取決於執行緒模型，如下表所示：  

  
|typedef|單一執行緒模型|Apartment 執行緒模型|免費的執行緒模型|  
|-------------|----------------------------|-------------------------------|--------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`;M = `CComMultiThreadModel`  
  
 `CComSingleThreadModel` 本身會定義三個**typedef**名稱。 `ThreadModelNoCS` 參考`CComSingleThreadModel`。 `AutoCriticalSection` 並`CriticalSection`reference 類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，可取得和釋放重要區段的擁有權與相關聯的空白方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComSingleThreadModel::AutoCriticalSection  
 使用時`CComSingleThreadModel`，則**typedef**名稱`AutoCriticalSection`參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>備註  
 因為`CComFakeCriticalSection`不會提供重要的區段，其方法會執行任何動作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)並[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定義`AutoCriticalSection`。 下表顯示執行緒的模型類別所參考的關鍵區段類別之間的關聯性`AutoCriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，您可以使用**typedef**名稱[CriticalSection](#criticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要消除 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="criticalsection"></a>  CComSingleThreadModel::CriticalSection  
 使用時`CComSingleThreadModel`，則**typedef**名稱`CriticalSection`參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>備註  
 因為`CComFakeCriticalSection`不會提供重要的區段，其方法會執行任何動作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)並[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定義`CriticalSection`。 下表顯示執行緒的模型類別所參考的關鍵區段類別之間的關聯性`CriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，您可以使用**typedef**名稱[AutoCriticalSection](#autocriticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要消除 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="decrement"></a>  CComSingleThreadModel::Decrement  
 此靜態函式會遞減變數的值所指向*p*。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 [in]要遞減之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 遞減的結果。  
  
##  <a name="increment"></a>  CComSingleThreadModel::Increment  
 此靜態函式會遞減變數的值所指向*p*。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 [in]要遞增之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 遞增值的結果。  
  
##  <a name="threadmodelnocs"></a>  CComSingleThreadModel::ThreadModelNoCS  
 使用時`CComSingleThreadModel`，則**typedef**名稱`ThreadModelNoCS`只是參考`CComSingleThreadModel`。  
  
```
typedef CComSingleThreadModel ThreadModelNoCS;
```  
  
### <a name="remarks"></a>備註  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)並[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含定義`ThreadModelNoCS`。 下表顯示執行緒的模型類別與所參考的類別之間的關聯性`ThreadModelNoCS`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
