---
title: "CComMultiThreadModelNoCS 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComMultiThreadModelNoCS
- CComMultiThreadModelNoCS
- ATL.CComMultiThreadModelNoCS
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: 18
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
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: dd14e5c941da5383dce19e9f7f539bfb9909759f
ms.lasthandoff: 02/28/2017

---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 類別
`CComMultiThreadModelNoCS`提供安全執行緒方法遞增和遞減變數的值，而不需要重要區段鎖定或解除鎖定功能。  
  
## <a name="syntax"></a>語法  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|參考類別`CComFakeCriticalSection`。|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|參考類別`CComMultiThreadModelNoCS`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|（靜態）遞減以執行緒安全的方式指定變數的值。|  
|[CComMultiThreadModelNoCS::Increment](#increment)|（靜態）遞增特定變數的值以執行緒安全的方式。|  
  
## <a name="remarks"></a>備註  
 `CComMultiThreadModelNoCS`類似於[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) ，因為它提供安全執行緒方法遞增和遞減的變數。 不過，當您參考重要區段類別，透過`CComMultiThreadModelNoCS`，方法如`Lock`和`Unlock`會執行任何動作。  
  
 您通常會使用`CComMultiThreadModelNoCS`透過`ThreadModelNoCS``typedef`名稱。 這`typedef`定義於`CComMultiThreadModelNoCS`， `CComMultiThreadModel`，和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)。  
  
> [!NOTE]
>  全域`typedef`名稱[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)不會參考`CComMultiThreadModelNoCS`。  
  
 除了`ThreadModelNoCS`，`CComMultiThreadModelNoCS`定義`AutoCriticalSection`和`CriticalSection`。 這些後面兩者`typedef`名稱參考[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，它會提供空的方法，取得和釋放重要區段相關聯。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-nameautocriticalsectiona--ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection  
 當使用`CComMultiThreadModelNoCS`、`typedef`名稱`AutoCriticalSection`參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>備註  
 因為`CComFakeCriticalSection`不會提供重要區段，其方法不會執行任何動作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含定義`AutoCriticalSection`。 下表顯示執行緒模型類別所參考的重要區段類別之間的關聯性`AutoCriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，您可以使用`typedef`名稱[CriticalSection](#criticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要刪除的 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="a-namecriticalsectiona--ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection  
 當使用`CComMultiThreadModelNoCS`、`typedef`名稱`CriticalSection`參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>備註  
 因為`CComFakeCriticalSection`不會提供重要區段，其方法不會執行任何動作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含定義`CriticalSection`。 下表顯示執行緒模型類別所參考的重要區段類別之間的關聯性`CriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，您可以使用`typedef`名稱`AutoCriticalSection`。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要刪除的 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="a-namedecrementa--ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::Decrement  
 靜態函式呼叫 Win32 函式[InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580)，所指向的變數值的遞減`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]要遞減之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果遞減的結果是 0，則`Decrement`會傳回 0。 如果遞減的結果為非零，傳回值也是為非零，但是可能不等於遞減的結果。  
  
### <a name="remarks"></a>備註  
 **InterlockedDecrement**防止多個執行緒同時使用此變數。  
  
##  <a name="a-nameincrementa--ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Increment  
 靜態函式呼叫 Win32 函式[InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614)，其中增加所指向之變數的值`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]要遞增之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果增量的結果是 0，則**遞增**會傳回 0。 如果增量的結果為非零，傳回值也是為非零，但是可能不會等於增量的結果。  
  
### <a name="remarks"></a>備註  
 **InterlockedIncrement**防止多個執行緒同時使用此變數。  
  
##  <a name="a-namethreadmodelnocsa--ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS  
 當使用`CComMultiThreadModelNoCS`、`typedef`名稱`ThreadModelNoCS`只是參考`CComMultiThreadModelNoCS`。  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>備註  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含定義`ThreadModelNoCS`。 下表顯示執行緒模型類別與所參考的類別之間的關聯性`ThreadModelNoCS`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 請注意，定義`ThreadModelNoCS`中`CComMultiThreadModelNoCS`提供與對稱性`CComMultiThreadModel`和`CComSingleThreadModel`。 例如，假設的範例程式碼`CComMultiThreadModel::AutoCriticalSection`宣告下列`typedef`:  
  
 [!code-cpp[NVC_ATL_COM&#37;](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 不論指定的類別`ThreadModel`(例如`CComMultiThreadModelNoCS`)，`_ThreadModel`隨之解決。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
