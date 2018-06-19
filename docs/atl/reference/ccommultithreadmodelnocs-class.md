---
title: CComMultiThreadModelNoCS 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 758811b10757cd7903b4f1d6218a5f34f8a98462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364189"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 類別
`CComMultiThreadModelNoCS` 提供安全執行緒方法遞增和遞減變數的值，而不需要重要區段的鎖定或解除鎖定功能。  
  
## <a name="syntax"></a>語法  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|參考類別`CComFakeCriticalSection`。|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|參考類別`CComMultiThreadModelNoCS`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|（靜態）遞減以執行緒安全的方式指定變數的值。|  
|[CComMultiThreadModelNoCS::Increment](#increment)|（靜態）以執行緒安全的方式遞增指定變數的值。|  
  
## <a name="remarks"></a>備註  
 `CComMultiThreadModelNoCS` 類似於[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) ，因為它提供安全執行緒方法遞增和遞減的變數。 不過，當您參考關鍵區段類別透過`CComMultiThreadModelNoCS`，這類方法`Lock`和`Unlock`不執行任何動作。  
  
 通常，您會使用`CComMultiThreadModelNoCS`透過`ThreadModelNoCS``typedef`名稱。 這`typedef`中定義`CComMultiThreadModelNoCS`， `CComMultiThreadModel`，和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)。  
  
> [!NOTE]
>  全域`typedef`名稱[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)不會參考`CComMultiThreadModelNoCS`。  
  
 除了`ThreadModelNoCS`，`CComMultiThreadModelNoCS`定義`AutoCriticalSection`和`CriticalSection`。 這些後面兩者`typedef`名稱參考[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，這樣會提供與取得和釋放重要區段相關聯的空白方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection  
 當使用`CComMultiThreadModelNoCS`、`typedef`名稱`AutoCriticalSection`參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>備註  
 因為`CComFakeCriticalSection`不提供重要的區段，其方法會執行任何動作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含定義`AutoCriticalSection`。 下表顯示執行緒模型類別所參考的重要區段類別之間的關聯性`AutoCriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，您可以使用`typedef`名稱[CriticalSection](#criticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要排除 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection  
 當使用`CComMultiThreadModelNoCS`、`typedef`名稱`CriticalSection`參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>備註  
 因為`CComFakeCriticalSection`不提供重要的區段，其方法會執行任何動作。  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含定義`CriticalSection`。 下表顯示執行緒模型類別所參考的重要區段類別之間的關聯性`CriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，您可以使用`typedef`名稱`AutoCriticalSection`。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要排除 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement  
 此靜態函式會呼叫 Win32 函式[InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580)，變數的值所指向的遞減`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]要遞減之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果遞減的結果為 0，則`Decrement`傳回 0。 如果遞減的結果為非零，傳回值也為非零，但可能不等於遞減的結果。  
  
### <a name="remarks"></a>備註  
 **InterlockedDecrement**防止多個執行緒同時使用此變數。  
  
##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment  
 此靜態函式會呼叫 Win32 函式[InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614)，其中變數所指向的值遞增`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]要遞增之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果增量的結果為 0，則**遞增**傳回 0。 如果增量的結果為非零，傳回值也為非零值，但可能不會等於增量的結果。  
  
### <a name="remarks"></a>備註  
 **InterlockedIncrement**防止多個執行緒同時使用此變數。  
  
##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS  
 當使用`CComMultiThreadModelNoCS`、`typedef`名稱`ThreadModelNoCS`只是參考`CComMultiThreadModelNoCS`。  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>備註  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含定義`ThreadModelNoCS`。 下表顯示執行緒模型類別所參考類別之間的關聯性`ThreadModelNoCS`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 請注意，定義`ThreadModelNoCS`中`CComMultiThreadModelNoCS`提供與對稱性`CComMultiThreadModel`和`CComSingleThreadModel`。 例如，假設中的範例程式碼`CComMultiThreadModel::AutoCriticalSection`宣告下列`typedef`:  
  
 [!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 不論指定的類別`ThreadModel`(例如`CComMultiThreadModelNoCS`)，`_ThreadModel`隨之解決。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)