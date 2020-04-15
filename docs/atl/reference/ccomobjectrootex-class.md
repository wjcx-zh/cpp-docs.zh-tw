---
title: CComObjectRootEx 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: e8db86f6214f95cd9bb08d3b5f6c6c1a38ca475c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327598"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx 類別

此類提供了處理非聚合物件和聚合物件的物件引用計數管理的方法。

## <a name="syntax"></a>語法

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>參數

*螺紋模型*<br/>
其方法實現所需線程模型的類。 您可以通過將*線程模型*設置為[CCom 單線程模型](../../atl/reference/ccomsinglethreadmodel-class.md)[、CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)來顯式選擇線程模型。 通過將*ThreadModel*設置為[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel,](atl-typedefs.md#ccomglobalsthreadmodel)可以接受伺服器的預設線程模型。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|建構函式。|
|[內部新增參考](#internaladdref)|增加非聚合物件的引用計數。|
|[內部發佈](#internalrelease)|取消非聚合物件的引用計數。|
|[鎖](#lock)|如果線程模型是多線程的,則獲取關鍵部分物件的擁有權。|
|[解除鎖定](#unlock)|如果線程模型是多線程的,則釋放關鍵部分物件的擁有權。|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootbase 方法

|||
|-|-|
|[最終建構](#finalconstruct)|在類中重寫以執行物件所需的任何初始化。|
|[最終發佈](#finalrelease)|在類中重寫以執行物件所需的任何清理。|
|[外加參照](#outeraddref)|增加聚合物件的引用計數。|
|[外部查詢介面](#outerqueryinterface)|表示到聚合物件的`IUnknown`外部。|
|[外部釋放](#outerrelease)|取消聚合物件的引用計數。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[內部查詢介面](#internalqueryinterface)|委託給`IUnknown`非聚合物件的。|
|[物件主](#objectmain)|在模組初始化和物件映射中列出的派生類終止期間調用。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_dwRef](#m_dwref)|與`m_pOuterUnknown`, 工會的一部分。 當物件未聚合以保存和`AddRef``Release`的引用計數時使用。|
|[m_pOuterUnknown](#m_pouterunknown)|與`m_dwRef`, 工會的一部分。 當物件聚合以保存指向外部未知指標時使用。|

## <a name="remarks"></a>備註

`CComObjectRootEx`處理非聚合物件和聚合物件的物件引用計數管理。 如果物件未聚合,它將保存物件引用計數,並且保留指向外部未知物件的指標(如果物件正在聚合)。 對於聚合物件,`CComObjectRootEx`可以使用方法來處理內部物件構造的失敗,並在釋放內部介面或刪除內部物件時保護外部物件不被刪除。

從 COM 伺服器的類別`CComObjectRootEx`必須繼承或[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)。

如果類定義指定[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)宏,ATL 將創建`CComPolyObject<CYourClass>``IClassFactory::CreateInstance`調用時 的實例。 在創建期間,將檢查外部未知值。 如果為 NULL,`IUnknown`則為非聚合物件實現。 如果外部未知值不是 NULL,`IUnknown`則為聚合對象實現。

如果類未指定DECLARE_POLY_AGGREGATABLE宏,ATL`CAggComObject<CYourClass>`將創建聚合物件的實例`CComObject<CYourClass>`或 非聚合物件的實例。

使用`CComPolyObject`的優點是,您避免在模組`CComAggObject``CComObject`中同時處理聚合和非聚合情況。 單個`CComPolyObject`物件處理這兩種情況。 因此,模組中僅存在一個 vtable 副本和函數副本。 如果 vtable 很大,這可大幅減小模組大小。 但是,如果 vtable 很小`CComPolyObject`,則使用可能會導致模組大小稍大一些,因為它未針對聚合或非聚合物件進行優化`CComAggObject`,`CComObject`例如和 。

如果物件是聚合的,[則 IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)`CComAggObject`由`CComPolyObject`或 實現。 這些類別的`QueryInterface``AddRef`委託`Release`與呼`CComObjectRootEx`叫`OuterQueryInterface`的`OuterAddRef`,`OuterRelease`並轉發到外部未知。 通常,在類`CComObjectRootEx::FinalConstruct`中重寫以創建任何聚合物件,並重`CComObjectRootEx::FinalRelease`寫 以釋放任何聚合物件。

如果物件未聚合,`IUnknown`則`CComObject`由`CComPolyObject`或實現。 在這種情況下,`QueryInterface`對`AddRef``Release`的調用 將`CComObjectRootEx`委`InternalQueryInterface``InternalAddRef`派給`InternalRelease`的 , 以及執行實際操作。

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootEx:CComObjectRootEx

建構函數將引用計數初始化為 0。

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx:最終建構

可以在派生類中重寫此方法,以執行物件所需的任何初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

返回成功時S_OK或標準錯誤 HRESULT 值之一。

### <a name="remarks"></a>備註

預設情況下,`CComObjectRootEx::FinalConstruct`只需返回S_OK。

在 類別`FinalConstruct`執行初始化的優點,而不是類的建構函數:

- 您不能從建構函數返回狀態代碼,但可以`FinalConstruct`通過的返回值返回 HRESULT。 使用 ATL 提供的標準類工廠創建類的物件時,此返回值將傳播回 COM 客戶端,從而允許您向他們提供詳細的錯誤資訊。

- 不能通過類的構造函數調用虛擬函數機制。 從類的構造函數調用虛擬函數會導致對函數的靜態解析調用,因為它在繼承層次結構中定義。 對純虛擬函數的調用會導致連結器錯誤。

   類不是繼承層次結構中派生最多的類 - 它依賴於 ATL 提供的派生類來提供其某些功能。 初始化很可能需要使用該類提供的要素(當類的物件需要聚合其他物件時,情況確實如此),但類中的構造函數無法訪問這些要素。 在完全構造最派生的類之前,將執行類的構造代碼。

   但是,`FinalConstruct`在完全建構最派生的類後立即調用,允許您調用虛擬函數並使用 ATL 提供的引用計數實現。

### <a name="example"></a>範例

通常,在派生的`CComObjectRootEx`類中重寫此方法以創建任何聚合物件。 例如：

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

如果建構失敗,您可以傳回錯誤。 如果內部聚合物件在創建過程中增加引用計數,然後將計數化為 0,則可以使用宏[DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct)來保護外部物件不被刪除。

以下是建立聚合的典型方法:

- 向類`IUnknown`物件添加指標,並將其初始化到建構函數中的 NULL。

- 重寫`FinalConstruct`以創建聚合。

- 使用定義為`IUnknown`參數的指標[,COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate)宏。

- 重寫`FinalRelease`以`IUnknown`釋放指標。

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx:最終發佈

可以在派生類中重寫此方法,以執行物件所需的任何清理。

```
void FinalRelease();
```

### <a name="remarks"></a>備註

預設情況下,`CComObjectRootEx::FinalRelease`不執行任何操作。

執行清理`FinalRelease`比向類的析構函數添加代碼更可取,因為物件仍在調用`FinalRelease`的 點完全構造。 這使您能夠安全地訪問最派生類提供的方法。 這對刪除之前釋放任何聚合物件尤其重要。

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx::內部AddRef

將非聚合物件的引用計數增加1。

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>傳回值

可用於診斷和測試的值。

### <a name="remarks"></a>備註

如果線程模型是多線程的,`InterlockedIncrement`則用於防止多個線程同時更改引用計數。

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx:內部查詢介面

擷取所要求介面的指標。

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*p*<br/>
[在]指向物件的指標,其中包含向 公開的介面的 COM`QueryInterface`映射 。

*p 項目*<br/>
[在]指向訪問可用介面`_ATL_INTMAP_ENTRY`對應的結構的指標。

*Iid*<br/>
[在]請求的介面的 GUID。

*ppvObject*<br/>
[出]指向*iid*中指定的介面指標,如果找不到介面,則指向 NULL 中的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

`InternalQueryInterface` 只處理 COM 對應表格中的介面。 如果物件是聚合的,`InternalQueryInterface`則不委託給外部未知物件。 您可以使用巨[集COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其變體之一在 COM 地圖表中輸入介面。

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx:內部發佈

將非聚合物件的引用計數減少 1。

```
ULONG InternalRelease();
```

### <a name="return-value"></a>傳回值

在非調試和調試生成中,此函數返回一個可用於診斷或測試的值。 返回的確切值取決於許多因素,如使用的操作系統,並且可能是引用計數,也可能不是。

### <a name="remarks"></a>備註

如果線程模型是多線程的,`InterlockedDecrement`則用於防止多個線程同時更改引用計數。

## <a name="ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx:鎖定

如果線程模型是多線程的,此方法將調用 Win32 API 函數[EnterDataSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection),它等待線程可以取得通過私有數據成員獲得的關鍵部分物件的擁有權。

```
void Lock();
```

### <a name="remarks"></a>備註

當受保護的代碼完成執行時,線程必須調用`Unlock`以釋放關鍵部分的擁有權。

如果線程模型是單線程的,則此方法不執行任何操作。

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a>CComObjectRootEx:m_dwRef

訪問四個字節記憶體的聯合的一部分。

```
long m_dwRef;
```

### <a name="remarks"></a>備註

使用`m_pOuterUnknown`,聯合的一部分:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果未聚合物件,則`AddRef``Release`和訪問的引用計數將存儲在中。 `m_dwRef` 如果對象是聚合的,則指向外部未知值的指標存儲在[m_pOuterUnknown](#m_pouterunknown)中。

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown

訪問四個字節記憶體的聯合的一部分。

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>備註

使用`m_dwRef`,聯合的一部分:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

如果對象是聚合的,則指向外部未知值的指標存儲在`m_pOuterUnknown`中。 如果未聚合物件,則訪問`AddRef`和`Release`的引用計數存儲在[m_dwRef](#m_dwref)中。

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx:物件Main

對於物件映射中列出的每個類,在初始化模組時調用此函數一次,在終止模組時再次調用該函數。

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>參數

*b 開始*<br/>
[出]如果要初始化類,則該值為 TRUE;如果正在初始化該類,則該值為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

*bStarting*參數的值指示模組是初始化還是終止。 的`ObjectMain`預設實現不執行任何操作,但您可以重寫類中的此函數,以初始化或清理要為類分配的資源。 請注意,`ObjectMain`在請求類的任何實例之前調用。

`ObjectMain`從 DLL 的入口點調用,因此入口點函數可以執行的操作類型受到限制。 有關這些限制的詳細資訊,請參閱[DLL 和 VisualC++執行時庫行為](../../build/run-time-library-behavior.md)與[DllMain](/windows/win32/Dlls/dllmain)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootEx::外部AddRef

遞增聚合的外部未知數。

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>傳回值

可用於診斷和測試的值。

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx:外部查詢介面

檢索指向請求的介面的間接指標。

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]請求的介面的 GUID。

*ppvObject*<br/>
[出]指向*iid*中指定的介面指標,如果聚合不支援介面,則指向 NULL 中的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx:外部釋放

取消聚合外部未知項的引用計數。

```
ULONG OuterRelease();
```

### <a name="return-value"></a>傳回值

在非調試生成中,始終返回 0。 在調試生成中,返回可用於診斷或測試的值。

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx:解鎖

如果線程模型是多線程的,此方法調用 Win32 API 函數[Leave臨界節](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection),它釋放通過私有數據成員獲取的關鍵部分物件的擁有權。

```
void Unlock();
```

### <a name="remarks"></a>備註

要取得所有權,線程必須呼叫`Lock`。 每個調用`Lock`都需要相應的調用`Unlock`以 釋放關鍵部分的擁有權。

如果線程模型是單線程的,則此方法不執行任何操作。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPoly 物件類別](../../atl/reference/ccompolyobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
