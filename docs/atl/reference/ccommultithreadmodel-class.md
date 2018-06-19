---
title: CComMultiThreadModel 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a89af8507150ee708ad381be2d47201c9266f763
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364538"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 類別
`CComMultiThreadModel` 提供具備執行緒安全的方法來遞增和遞減變數的值。  
  
## <a name="syntax"></a>語法  
  
```
class CComMultiThreadModel
```  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|參考類別[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|  
|[CComMultiThreadModel::CriticalSection](#criticalsection)|參考類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|  
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|參考類別[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](#decrement)|（靜態）遞減以執行緒安全的方式指定變數的值。|  
|[CComMultiThreadModel::Increment](#increment)|（靜態）以執行緒安全的方式遞增指定變數的值。|  
  
## <a name="remarks"></a>備註  
 通常，您會使用`CComMultiThreadModel`透過下列其中兩個`typedef`名稱，其中一個 [CComObjectThreadModel] (atl typedefs.md #ccomobjectthreadmodel 或 [CComGlobalsThreadModel] (atl typedefs.md #ccomglobalsthreadmodel。 每個參考類別`typedef`取決於使用的執行緒模型下, 表所示：  
  
|typedef|單一執行緒處理|Apartment 執行緒|無限制執行緒|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`;M = `CComMultiThreadModel`  
  
 `CComMultiThreadModel` 本身定義三個`typedef`名稱。 `AutoCriticalSection` 和`CriticalSection`參考提供方法來取得及釋放關鍵區段的擁有權的類別。 `ThreadModelNoCS` 參考類別 [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection  
 當使用`CComMultiThreadModel`、`typedef`名稱`AutoCriticalSection`參考類別[CComAutoCriticalSection](ccomautocriticalsection-class.md)，可提供方法取得和釋放重要區段物件的擁有權。  
  
```
typedef CComAutoCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>備註  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含定義`AutoCriticalSection`。 下表顯示執行緒模型類別所參考的重要區段類別之間的關聯性`AutoCriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`AutoCriticalSection`，您可以使用`typedef`名稱[CriticalSection](#criticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要排除 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 下列程式碼會建立模型之後[CComObjectRootEx](ccomobjectrootex-class.md)，並示範`AutoCriticalSection`執行緒環境中使用。  
  

```cpp  
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);   
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```  
  
 下表顯示的結果`InternalAddRef`和`Lock`方法，取決於**ThreadModel**樣板參數和應用程式所使用的執行緒模型：  
  
### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel  
  
|方法|使用 single 或 Apartment 執行緒|無限制執行緒|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|增量不具備執行緒安全。|增量是安全執行緒。|  
|`Lock`|沒有任何作用。沒有任何鎖定的重要區段。|關鍵區段已鎖定。|  
  
### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS  
  
|方法|使用 single 或 Apartment 執行緒|無限制執行緒|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|增量不具備執行緒安全。|增量是安全執行緒。|  
|`Lock`|沒有任何作用。沒有任何鎖定的重要區段。|沒有任何作用。沒有任何鎖定的重要區段。|  
  
##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection  
 當使用`CComMultiThreadModel`、`typedef`名稱`CriticalSection`參考類別[CComCriticalSection](ccomcriticalsection-class.md)，可提供方法取得和釋放重要區段物件的擁有權。  
  
```
typedef CComCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>備註  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含定義`CriticalSection`。 下表顯示執行緒模型類別所參考的重要區段類別之間的關聯性`CriticalSection`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 除了`CriticalSection`，您可以使用`typedef`名稱[AutoCriticalSection](#autocriticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要排除 CRT 啟始程式碼中。  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。  
  
##  <a name="decrement"></a>  CComMultiThreadModel::Decrement  
 此靜態函式會呼叫 Win32 函式[InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580)，變數的值所指向的遞減`p`。  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]要遞減之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果遞減的結果為 0，則`Decrement`傳回 0。 如果遞減的結果為非零，傳回值也為非零，但可能不等於遞減的結果。  
  
### <a name="remarks"></a>備註  
 **InterlockedDecrement**防止多個執行緒同時使用此變數。  
  
##  <a name="increment"></a>  CComMultiThreadModel::Increment  
 此靜態函式會呼叫 Win32 函式[InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614)，其中變數所指向的值遞增`p`。  
  
```
static ULONG WINAPI Increment(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]要遞增之變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果增量的結果為 0，則**遞增**傳回 0。 如果增量的結果為非零，傳回值也為非零值，但可能不會等於增量的結果。  
  
### <a name="remarks"></a>備註  
 **InterlockedIncrement**防止多個執行緒同時使用此變數。  
  
##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS  
 當使用`CComMultiThreadModel`、`typedef`名稱`ThreadModelNoCS`參考類別[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>備註  
 `CComMultiThreadModelNoCS` 提供安全執行緒方法遞增和遞減的變數。不過，它不提供重要區段。  
  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md)和`CComMultiThreadModelNoCS`也包含定義`ThreadModelNoCS`。 下表顯示執行緒模型類別所參考類別之間的關聯性`ThreadModelNoCS`:  
  
|在定義類別|參考類別|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>範例  
 請參閱[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。  
  
## <a name="see-also"></a>另請參閱  
 [CComSingleThreadModel 類別](ccomsinglethreadmodel-class.md)   
 [CComAutoCriticalSection 類別](ccomautocriticalsection-class.md)   
 [CComCriticalSection 類別](ccomcriticalsection-class.md)   
 [類別概觀](../atl-class-overview.md)
