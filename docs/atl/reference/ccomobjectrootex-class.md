---
title: "CComObjectRootEx 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComObjectRootEx
- ATL::CComObjectRootEx<ThreadModel>
- CComObjectRootEx
- ATL::CComObjectRootEx
- ATL.CComObjectRootEx<ThreadModel>
dev_langs:
- C++
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
caps.latest.revision: 20
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
ms.openlocfilehash: f3a6d26ddb4f612824f959ca3046531dc3bbf2a9
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 類別
這個類別會提供用來處理非彙總及彙總物件的物件參考計數管理方法。  
  
## <a name="syntax"></a>語法  
  
```
template<class ThreadModel>  
class CComObjectRootEx : public CComObjectRootBase
```  
  
#### <a name="parameters"></a>參數  
 `ThreadModel`  
 類別，其方法實作所需的執行緒模型。 您可以明確選擇的執行緒模型設定`ThreadModel`至[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)， [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。 您可以藉由設定接受伺服器的預設執行緒模型`ThreadModel`至[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)。  

  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CComObjectRootEx](#ccomobjectrootex)|建構函式。|  
|[InternalAddRef](#internaladdref)|非彙總物件的參考計數遞增。|  
|[InternalRelease](#internalrelease)|遞減參考計數的非彙總的物件。|  
|[鎖定](#lock)|如果是多執行緒的執行緒模型，會取得重要區段物件的擁有權。|  
|[解除鎖定](#unlock)|如果是多執行緒的執行緒模型，會釋放重要區段物件的擁有權。|  
  
### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase 方法  
  
|||  
|-|-|  
|[FinalConstruct](#finalconstruct)|在您執行您的物件所需的任何初始化的類別中覆寫。|  
|[FinalRelease](#finalrelease)|在您執行您的物件所需的任何清除作業的類別中覆寫。|  
|[OuterAddRef](#outeraddref)|彙總物件的參考計數遞增。|  
|[OuterQueryInterface](#outerqueryinterface)|委派至外部**IUnknown**的彙總的物件。|  
|[OuterRelease](#outerrelease)|遞減參考計數的彙總的物件。|  
  
### <a name="static-functions"></a>靜態函式  
  
|||  
|-|-|  
|[InternalQueryInterface](#internalqueryinterface)|委派給**IUnknown**的非彙總的物件。|  
|[ObjectMain](#objectmain)|在模組初始化及終止的物件對應中所列的衍生類別呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_dwRef](#m_dwref)|使用`m_pOuterUnknown`、 聯集的一部分。 當物件不會彙總來保存的參考計數時，使用`AddRef`和**版本**。|  
|[m_pOuterUnknown](#m_pouterunknown)|使用`m_dwRef`、 聯集的一部分。 物件會保留指標外部彙總時使用。|  
  
## <a name="remarks"></a>備註  
 `CComObjectRootEx`處理非彙總及彙總物件的物件參考計數管理。 如果您的物件不會被彙總，而且存放的外部未知的指標，如果您的物件正在彙總，它會保留物件參考計數。 對於彙總的物件，`CComObjectRootEx`方法可用來處理失敗，內部物件的建構，而且要保護以防止內部介面發行時刪除外部物件或內部的物件已刪除。  
  
 實作 COM 伺服器的類別必須繼承自`CComObjectRootEx`或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。  
  
 如果您的類別定義指定[DECLARE_POLY_AGGREGATABLE](http://msdn.microsoft.com/library/7569e738-cfbc-4404-ba1d-78dcefa3bdb3)巨集，ATL 建立的執行個體**CComPolyObject\<CYourClass >**時**iclassfactory:: Createinstance**呼叫。 在建立期間，會檢查的外部未知的值。 如果是**NULL**， **IUnknown**實作非彙總的物件。 如果不是外部的未知**NULL**， **IUnknown**彙總物件實作。  
  
 如果您的類別未指定`DECLARE_POLY_AGGREGATABLE`巨集，ATL 建立的執行個體**CAggComObject\<CYourClass >**彙總的物件或執行個體的**CComObject\<CYourClass >**非彙總的物件。  
  
 使用的優點`CComPolyObject`是，您不需要同時`CComAggObject`和`CComObject`模組處理彙總及非彙總的情況。 單一`CComPolyObject`物件會處理這兩種情況。 因此，vtable 只有一個複本，以及一份函式存在您的模組。 如果您的 vtable 很大，這可大幅減少模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`可能會導致較大的模組大小，因為沒有最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。  
  
 如果您的物件會彙總， [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)由實作`CComAggObject`或`CComPolyObject`。 這些類別委派`QueryInterface`， `AddRef`，和**版本**呼叫`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`轉送給的外部未知。 通常，您會覆寫`CComObjectRootEx::FinalConstruct`在類別中建立任何彙總的物件，並覆寫`CComObjectRootEx::FinalRelease`來釋放任何彙總物件。  
  
 如果您的物件不會彙總， **IUnknown**由實作`CComObject`或`CComPolyObject`。 在此情況下，呼叫`QueryInterface`， `AddRef`，和**版本**委派給`CComObjectRootEx`的`InternalQueryInterface`， `InternalAddRef`，和`InternalRelease`來執行實際的操作。  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-nameccomobjectrootexa--ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx  
 建構函式會初始化為 0 的參考計數。  
  
```
CComObjectRootEx();
```  
  
##  <a name="a-namefinalconstructa--ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct  
 您可以執行您的物件所需的任何初始化衍生類別中覆寫這個方法。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`成功或其中一個標準錯誤`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 根據預設，`CComObjectRootEx::FinalConstruct`只會傳回`S_OK`。  
  
 有執行中的初始設定的優點`FinalConstruct`而不是類別的建構函式︰  
  
-   您無法從建構函式，傳回狀態碼，但是您可以傳回`HRESULT`藉由`FinalConstruct`的傳回值。 當正在使用 ATL 所提供的標準 class factory 建立類別的物件時，此傳回值會傳播回 COM 用戶端可讓您提供詳細的錯誤資訊。  
  
-   您無法透過虛擬函式機制，從類別的建構函式呼叫虛擬函式。 在該點定義繼承階層架構中，從類別的建構函式呼叫虛擬函式產生的函式以統計方式解析呼叫。 純虛擬函式的呼叫會導致連結器錯誤。  
  
     您的類別不是最具衍生性的類別階層架構中，它會依賴 ATL 提供某些功能所提供的衍生類別。 可能需要您初始化使用 （特別是當您的類別物件需要彙總的其他物件） 該類別所提供的功能，但在您的類別建構函式便無法存取這些功能。 您類別的建構程式碼執行之前完全建構最具衍生性的類別。  
  
     不過，`FinalConstruct`立即之後最多衍生類別完全建構可讓您呼叫虛擬函式，並使用提供的 ATL 參考計數的實作會呼叫  
  
### <a name="example"></a>範例  
 通常覆寫這個方法在類別中衍生自`CComObjectRootEx`建立任何彙總物件。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#40;](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]  
  
 如果建構失敗，您可以傳回錯誤。 您也可以使用巨集[DECLARE_PROTECT_FINAL_CONSTRUCT](http://msdn.microsoft.com/library/2d2e5ddc-057a-43ca-87c8-d3477a8193a0)來保護您的外部物件無法刪除，如果在建立期間，內部彙總的物件會遞增參考計數則遞減計數為 0。  
  
 以下是建立彙總的典型方式︰  
  
-   新增**IUnknown**指向您的類別物件，並將它初始化來**NULL**建構函式。  
  
-   覆寫`FinalConstruct`來建立彙總。  
  
-   使用**IUnknown**您定義做為參數的指標[COM_INTERFACE_ENTRY_AGGREGATE](http://msdn.microsoft.com/library/c671fa40-a57b-4797-ae88-c9762dabd4dc)巨集。  
  
-   覆寫`FinalRelease`釋放**IUnknown**指標。  
  
##  <a name="a-namefinalreleasea--ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx::FinalRelease  
 您可以執行任何清除作業所需的物件衍生類別中覆寫這個方法。  
  
```
void FinalRelease();
```  
  
### <a name="remarks"></a>備註  
 根據預設，`CComObjectRootEx::FinalRelease`不做任何動作。  
  
 執行中的清除工作`FinalRelease`最好在程式碼加入至類別的解構函式，因為物件仍然完整建構之起點在`FinalRelease`呼叫。 這可讓您安全地存取最具衍生性的類別所提供的方法。 這是特別重要，釋放之前刪除任何彙總的物件。  
  
##  <a name="a-nameinternaladdrefa--ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx::InternalAddRef  
 非彙總物件的參考計數遞增 1。  
  
```
ULONG InternalAddRef();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷和測試。  
  
### <a name="remarks"></a>備註  
 如果執行緒模型為多執行緒、 **InterlockedIncrement**用來防止多個執行緒同時變更參考計數。  
  
##  <a name="a-nameinternalqueryinterfacea--ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface  
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
 [in]包含的介面公開給 COM 對應物件的指標`QueryInterface`。  
  
 `pEntries`  
 [in]指標**_ATL_INTMAP_ENTRY**存取可用的介面對應的結構。  
  
 `iid`  
 [in]所要求介面的 GUID。  
  
 `ppvObject`  
 [out]在指定的介面指標的指標`iid`，或**NULL**如果找不到介面。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 `InternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件會彙總，`InternalQueryInterface`不會不會委派給外部未知。 您可以將介面輸入到 COM 對應表格使用巨集[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)或其中一個變化。  
  
##  <a name="a-nameinternalreleasea--ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx::InternalRelease  
 遞減參考計數的非彙總物件加 1。  
  
```
ULONG InternalRelease();
```  
  
### <a name="return-value"></a>傳回值  
 在同時非偵錯和偵錯組建，此函式傳回值，這個值可能是適用於診斷或測試。 確切的值取決於許多因素，例如作業系統使用，並可能，也可能不時，傳回做為參考計數。  
  
### <a name="remarks"></a>備註  
 如果執行緒模型為多執行緒、 **InterlockedDecrement**用來防止多個執行緒同時變更參考計數。  
  
##  <a name="a-namelocka--ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx::Lock  
 如果是多執行緒的執行緒模型，這個方法會呼叫 Win32 API 函式[EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608)，透過私用資料成員中取得的等候，直到執行緒可以取得重要區段物件的擁有權。  
  
```
void Lock();
```  
  
### <a name="remarks"></a>備註  
 當受保護的程式碼完成執行後時，必須呼叫執行緒`Unlock`釋放重要區段的擁有權。  
  
 如果執行緒模型為單一執行緒，這個方法沒有作用。  
  
##  <a name="a-namemdwrefa--ccomobjectrootexmdwref"></a><a name="m_dwref"></a>CComObjectRootEx::m_dwRef  
 存取記憶體的四個位元組的聯集的一部分。  
  
```
long m_dwRef;
```  
  
### <a name="remarks"></a>備註  
 使用`m_pOuterUnknown`、 聯集的一部分︰  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果物件不會彙總，由存取參考計數`AddRef`和**版本**會儲存在`m_dwRef`。 如果物件彙總，外部指標會儲存在[m_pOuterUnknown](#m_pouterunknown)。  
  
##  <a name="a-namempouterunknowna--ccomobjectrootexmpouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown  
 存取記憶體的四個位元組的聯集的一部分。  
  
```
IUnknown*
    m_pOuterUnknown;
```     
  
### <a name="remarks"></a>備註  
 使用`m_dwRef`、 聯集的一部分︰  
  
 `union`  
  
 `{`  
  
 `long m_dwRef;`  
  
 `IUnknown* m_pOuterUnknown;`  
  
 `};`  
  
 如果物件彙總，外部指標會儲存在`m_pOuterUnknown`。 如果物件不會彙總，由存取參考計數`AddRef`和**版本**會儲存在[m_dwRef](#m_dwref)。  
  
##  <a name="a-nameobjectmaina--ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx::ObjectMain  
 每個類別中列出[物件對應](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f)，一旦初始化模組時，會呼叫此函數並再次時它就會終止。  
  
```
static void WINAPI ObjectMain(bool bStarting);
```  
  
### <a name="parameters"></a>參數  
 `bStarting`  
 [out]值是**true**類別正在初始化，否則如果**false**。  
  
### <a name="remarks"></a>備註  
 值`bStarting`參數會指出是否將模組初始化或終止。 預設實作`ObjectMain`不做任何動作，但您可以在初始化或清除您想要的類別配置的資源類別中覆寫這個函式。 請注意，`ObjectMain`要求類別的任何執行個體之前，先呼叫。  
  
 `ObjectMain`會呼叫進入點的 DLL，所以受限制的進入點函式可以執行的作業類型。 如需有關這些限制的詳細資訊，請參閱[執行階段程式庫行為](../../build/run-time-library-behavior.md)和[DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#41;](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]  
  
##  <a name="a-nameouteraddrefa--ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootEx::OuterAddRef  
 參考計數遞增的彙總的外部未知。  
  
```
ULONG OuterAddRef();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷和測試。  
  
##  <a name="a-nameouterqueryinterfacea--ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface  
 擷取所要求介面的間接指標。  
  
```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求介面的 GUID。  
  
 `ppvObject`  
 [out]在指定的介面指標的指標`iid`，或**NULL**如果彙總不支援的介面。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
##  <a name="a-nameouterreleasea--ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx::OuterRelease  
 遞減參考計數的彙總的外部未知。  
  
```
ULONG OuterRelease();
```  
  
### <a name="return-value"></a>傳回值  
 在非偵錯組建中，一律傳回 0。 在偵錯組建中，傳回值，可能有助於診斷或測試。  
  
##  <a name="a-nameunlocka--ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx::Unlock  
 如果是多執行緒的執行緒模型，這個方法會呼叫 Win32 API 函式[LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169)，透過私用資料成員中取得重要區段物件的哪一個版本擁有權。  
  
```
void Unlock();
```  
  
### <a name="remarks"></a>備註  
 若要取得擁有權，必須呼叫執行緒`Lock`。 每次呼叫`Lock`需要對應的呼叫來`Unlock`釋放重要區段的擁有權。  
  
 如果執行緒模型為單一執行緒，這個方法沒有作用。  
  
## <a name="see-also"></a>另請參閱  
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 類別](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

