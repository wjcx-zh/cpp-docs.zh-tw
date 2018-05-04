---
title: CComObjectRootEx 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b147f0ad3f1a54c2ae640b6bf2426bcddf060b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 類別
這個類別會提供方法來處理非彙總及彙總物件的物件參考計數管理。  
  
## <a name="syntax"></a>語法  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>參數  
 `ThreadModel`  
 類別，其方法實作所需的執行緒模型。 您可以藉由設定明確選擇的執行緒模型`ThreadModel`至[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)， [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。 您可以藉由設定接受伺服器的預設執行緒模型`ThreadModel`至[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。  

  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|建構函式。|  
|[InternalAddRef](#internaladdref)|非彙總物件的參考計數遞增。|  
|[InternalRelease](#internalrelease)|遞減參考計數為非彙總的物件。|  
|[鎖定](#lock)|如果執行緒模型為多執行緒時，會取得重要區段物件的擁有權。|  
|[解除鎖定](#unlock)|如果執行緒模型為多執行緒時，會釋放重要區段物件的擁有權。|  
  
### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法  
  
|||  
|-|-|  
|[跖](#finalconstruct)|若要執行您的物件所需的任何初始化您類別中覆寫。|  
|[FinalRelease](#finalrelease)|執行您的物件所需的任何清除您類別中覆寫。|  
|[OuterAddRef](#outeraddref)|彙總物件的參考計數遞增。|  
|[OuterQueryInterface](#outerqueryinterface)|委派至外部**IUnknown**的彙總物件。|  
|[OuterRelease](#outerrelease)|遞減參考計數的彙總物件。|  
  
### <a name="static-functions"></a>靜態函式  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|委派給**IUnknown**的非彙總的物件。|  
|[ObjectMain](#objectmain)|在模組初始化及終止物件對應中列出的衍生類別呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|與`m_pOuterUnknown`聯集的一部分。 未保留參考計數的彙總物件時，使用`AddRef`和**發行**。|  
|[m_pOuterUnknown](#m_pouterunknown)|與`m_dwRef`聯集的一部分。 用來保存指標外部彙總物件時。|  
  
## <a name="remarks"></a>備註  
 `CComObjectRootEx` 處理非彙總與彙總物件的物件參考計數管理。 如果您的物件不會被彙總，而且存放的外部未知的指標，如果您的物件進行彙總，它會保留物件參考計數。 對於彙總物件，`CComObjectRootEx`方法可以用來處理失敗，內部物件的建構，並刪除保護以防止刪除內部介面發行時在外部物件或內部的物件。  
  
 實作的 COM 伺服器的類別必須繼承自`CComObjectRootEx`或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。  
  
 如果您的類別定義指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)巨集，ATL 建立的執行個體**CComPolyObject\<CYourClass >** 時**IClassFactory::CreateInstance**呼叫。 在建立期間，會檢查的外部未知的值。 如果是**NULL**， **IUnknown**實作非彙總的物件。 如果不是外部未知**NULL**， **IUnknown**彙總物件，則實作。  
  
 如果您的類別未指定`DECLARE_POLY_AGGREGATABLE`巨集，ATL 建立的執行個體**CAggComObject\<CYourClass >** 彙總的物件或執行個體的**Ccomobject<\<CYourClass>** 非彙總的物件。  
  
 使用的優點`CComPolyObject`是，您可以避免必須同時`CComAggObject`和`CComObject`處理彙總及非彙總的情況下在模組中。 單一`CComPolyObject`物件會處理這兩種情況。 因此，只能有一個複本 vtable 和一份函式存在於您可以在模組中。 如果您的 vtable 很大，這可以大幅降低模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`會造成較大的模組大小因為沒有最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。  
  
 如果您的物件彙總， [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)藉由`CComAggObject`或`CComPolyObject`。 這些類別委派`QueryInterface`， `AddRef`，和**發行**呼叫`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`轉送給的外部未知。 通常，您會覆寫`CComObjectRootEx::FinalConstruct`中建立任何彙總的物件，並覆寫類別`CComObjectRootEx::FinalRelease`來釋放任何彙總物件。  
  
 如果您的物件不會彙總， **IUnknown**藉由`CComObject`或`CComPolyObject`。 在此情況下，呼叫`QueryInterface`， `AddRef`，和**發行**委派給`CComObjectRootEx`的`InternalQueryInterface`， `InternalAddRef`，和`InternalRelease`執行實際的作業。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="ccomobjectrootex"></a>  CComObjectRootEx::CComObjectRootEx  
 建構函式會初始化為 0 的參考計數。  
  
```
CComObjectRootEx();
```  
  
##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct  
 您可以執行任何所需的物件進行初始化衍生類別中覆寫這個方法。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功，或其中一個標準錯誤`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 根據預設，`CComObjectRootEx::FinalConstruct`只會傳回`S_OK`。  
  
 有執行中的初始設定的優點`FinalConstruct`而不是類別的建構函式：  
  
-   您無法從建構函式，傳回狀態碼，但是您可以傳回`HRESULT`藉由`FinalConstruct`的傳回值。 您的類別物件在建立時使用 ATL 所提供的標準的 class factory，這個傳回值會傳播回到 COM 用戶端可讓您為他們提供詳細的錯誤資訊。  
  
-   您無法透過虛擬函式機制從類別的建構函式呼叫虛擬函式。 從類別的建構函式呼叫虛擬函式會導致以統計方式解析呼叫函式在該點定義繼承階層架構中。 純虛擬函式的呼叫會導致連結器錯誤。  
  
     您的類別不是最常衍生的類別階層架構中，它會仰賴在衍生類別所提供的某些功能，ATL 提供。 有很可能您初始化需要使用該類別 （這是確實需要彙總的其他物件類別的物件時），所提供的功能，但在您的類別建構函式無法存取這些功能。 您類別的建構程式碼執行之前完全建構最常衍生的類別。  
  
     不過，`FinalConstruct`稱為立即之後最多衍生類別完全建構可讓您呼叫虛擬函式，而使用參考計數所提供的實作 ATL  
  
### <a name="example"></a>範例  
 一般而言，覆寫這個方法中的類別衍生自`CComObjectRootEx`建立任何彙總物件。 例如:   
  
 [!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 如果建構失敗，您可以傳回錯誤。 您也可以使用巨集[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)來保護您的外部物件無法刪除，如果在建立時，內部彙總的物件會遞增參考計數則遞減計數設為 0。  
  
 以下是建立彙總的典型方式：  
  
-   新增**IUnknown**指向您的類別物件，並將它初始化來**NULL**建構函式中。  
  
-   覆寫`FinalConstruct`來建立彙總。  
  
-   使用**IUnknown**指標當做參數，以您定義[COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)巨集。  
  
-   覆寫`FinalRelease`釋放**IUnknown**指標。  
  
##  <a name="finalrelease"></a>  CComObjectRootEx::FinalRelease  
 您可以執行所有必要物件的清理衍生類別中覆寫這個方法。  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>備註  
 根據預設，`CComObjectRootEx::FinalRelease`不做任何動作。  
  
 執行中的清理`FinalRelease`偏好程式碼加入至類別的解構函式，因為物件仍然完整建構之起點在`FinalRelease`呼叫。 這可讓您安全地存取最常衍生的類別所提供的方法。 這是特別重要，釋放刪除之前的任何彙總的物件。  
  
##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef  
 非彙總物件的參考計數遞增 1。  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷和測試。  
  
### <a name="remarks"></a>備註  
 如果執行緒模型為多執行緒、 **InterlockedIncrement**用來防止多個執行緒同時變更參考計數。  
  
##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface  
 擷取所要求介面的指標。  
  
```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `pThis`  
 [in]包含的介面公開至 COM 對應物件的指標`QueryInterface`。  
  
 `pEntries`  
 [in]指標 **_ATL_INTMAP_ENTRY**存取的可用的介面對應的結構。  
  
 `iid`  
 [in]所要求介面的 GUID。  
  
 `ppvObject`  
 [out]中指定的介面指標的指標`iid`，或**NULL**如果找不到介面。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 `InternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件彙總，`InternalQueryInterface`不會不會委派給外部未知。 您可以將介面輸入到 COM 對應表格，使用巨集[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其中一個變數。  
  
##  <a name="internalrelease"></a>  CComObjectRootEx::InternalRelease  
 遞減參考計數的非彙總物件 1。  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>傳回值  
 在同時非偵錯和偵錯組建，此函式會傳回值，這可能有助於診斷或測試。 取決於許多因素，例如作業系統使用，並可能或可能不會傳回的確切的值，參考計數。  
  
### <a name="remarks"></a>備註  
 如果執行緒模型為多執行緒、 **InterlockedDecrement**用來防止多個執行緒同時變更參考計數。  
  
##  <a name="lock"></a>  CComObjectRootEx::Lock  
 如果執行緒模型為多執行緒，這個方法會呼叫 Win32 API 函式[EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608)，透過私用資料成員取得的等候，直到執行緒可以取得重要區段物件的擁有權。  
  
```
void Lock();
```  
  
### <a name="remarks"></a>備註  
 當受保護的程式碼完成執行後時，必須呼叫執行緒`Unlock`釋關鍵區段的擁有權。  
  
 如果執行緒模型為單一執行緒，這個方法沒有任何作用。  
  
##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef  
 存取記憶體的四個位元組的聯集的一部分。  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>備註  
 與`m_pOuterUnknown`聯集的一部分：  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果物件不會彙總，來存取參考計數`AddRef`和**發行**會儲存在`m_dwRef`。 如果已彙總物件的外部未知的指標會儲存在[m_pOuterUnknown](#m_pouterunknown)。  
  
##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown  
 存取記憶體的四個位元組的聯集的一部分。  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>備註  
 與`m_dwRef`聯集的一部分：  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果已彙總物件的外部未知的指標會儲存在`m_pOuterUnknown`。 如果物件不會彙總，來存取參考計數`AddRef`和**發行**會儲存在[m_dwRef](#m_dwref)。  
  
##  <a name="objectmain"></a>  CComObjectRootEx::ObjectMain  
 每個類別中所列[物件對應](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f)，一旦模組初始化時，呼叫此函式和再次時它就會終止。  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>參數  
 `bStarting`  
 [out]值是**true**類別正在初始化，否則如果**false**。  
  
### <a name="remarks"></a>備註  
 值`bStarting`參數會指出是否模組正在初始化或終止。 預設實作`ObjectMain`不做任何動作，但您可以在初始化或清除您想要的類別配置的資源類別中覆寫這個函式。 請注意，`ObjectMain`要求類別的任何執行個體之前呼叫。  
  
 `ObjectMain` 會呼叫 DLL 的進入點，因此的進入點函式可以執行的作業類型是受限制。 如需有關這些限制的詳細資訊，請參閱[Dll 和 Visual c + + 執行階段程式庫行為](../../build/run-time-library-behavior.md)和[DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef  
 遞增參考計數的彙總的外部未知。  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷和測試。  
  
##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface  
 擷取所要求介面的間接指標。  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求介面的 GUID。  
  
 `ppvObject`  
 [out]中指定的介面指標的指標`iid`，或**NULL**如果彙總不支援的介面。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
##  <a name="outerrelease"></a>  CComObjectRootEx::OuterRelease  
 遞減參考計數的彙總的外部未知。  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>傳回值  
 在非偵錯組建中，一律傳回 0。 在偵錯組建中，傳回值，可能有助於診斷或測試。  
  
##  <a name="unlock"></a>  CComObjectRootEx::Unlock  
 如果執行緒模型為多執行緒，這個方法會呼叫 Win32 API 函式[LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169)，透過私用資料成員取得哪些版本的擁有權的重要區段的物件。  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>備註  
 若要取得擁有權，必須呼叫執行緒`Lock`。 每次呼叫`Lock`需要對應呼叫`Unlock`釋關鍵區段的擁有權。  
  
 如果執行緒模型為單一執行緒，這個方法沒有任何作用。  
  
## <a name="see-also"></a>另請參閱  
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [Ccomobject< 類別](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
