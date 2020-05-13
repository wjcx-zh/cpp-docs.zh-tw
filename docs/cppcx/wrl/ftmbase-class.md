---
title: FtmBase 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: d37cdddda8cf8894016ed80b9055fe106b1600f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371506"
---
# <a name="ftmbase-class"></a>FtmBase 類別

代表無限制執行緒封送處理器物件。

## <a name="syntax"></a>語法

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>備註

有關詳細資訊,請參閱[執行時類](runtimeclass-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱                         | 描述                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase::FtmBase](#ftmbase) | 將 `FtmBase` 類別的新執行個體初始化。 |

### <a name="public-methods"></a>公用方法

| 名稱                                                               | 描述                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::建立全域介面表](#createglobalinterfacetable) | 創建全域介面表 (GIT)。                                                                                                                              |
| [FtmBase::D連線物件](#disconnectobject)                     | 強制釋放到物件的所有外部連接。 在關閉之前,對象的伺服器調用該物件的此方法的實現。                |
| [FtmBase:獲取元帥SizeMax](#getmarshalsizemax)                   | 獲取在指定物件上封送指定介面指標所需的位元組數的上限。                                                |
| [FtmBase:取得 Unmarshal 類](#getunmarshalclass)                   | 取得 COM 用於查找包含相應代理程式碼的 DLL 的 CLSID。 COM 載入此 DLL 以建立代理的未初始化實體。 |
| [FtmBase::MarshalInterface](#marshalinterface)                     | 將在某些用戶端進程中初始化代理物件所需的數據寫入流中。                                                                          |
| [FtmBase::釋放元帥數據](#releasemarshaldata)                 | 銷毀封送的數據包。                                                                                                                                    |
| [FtmBase:取消封送介面](#unmarshalinterface)                 | 初始化新創建的代理並返回指向該代理的介面指標。                                                                                    |

### <a name="public-data-members"></a>公用資料成員

| 名稱                                | 描述                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase:marshaller_](#marshaller) | 保存對自由線程封送器的引用。 |

## <a name="inheritance-hierarchy"></a>繼承階層架構

`FtmBase`

## <a name="requirements"></a>需求

**標題:** ftm.h

**命名空間：** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase::建立全域介面表

創建全域介面表 (GIT)。

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>參數

*Git*<br/>
此操作完成後,將指標指向全域介面表。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 MSDN`IGlobalInterfaceTable``COM Reference`庫`COM Interfaces`中 主題 子主題中的主題。

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase::D連線物件

強制釋放到物件的所有外部連接。 在關閉之前,對象的伺服器調用該物件的此方法的實現。

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>參數

*dw 保留*<br/>
保留以備將來之用；必須為零。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>FtmBase::FtmBase

將 `FtmBase` 類別的新執行個體初始化。

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase:獲取元帥SizeMax

獲取在指定物件上封送指定介面指標所需的位元組數的上限。

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>參數

*riid*<br/>
對要封送的介面的標識符的引用。

*光伏*<br/>
要封送的介面指標;可以是 NULL。

*dwDest 上下文*<br/>
要取消封送指定介面的目標上下文。

指定一個或多個 MSHCTX 枚舉值。

目前,取消封送可能發生在當前進程的另一個單元(MSHCTX_INPROC),也可以與當前進程 (MSHCTX_LOCAL) 在同一台計算機上的另一個進程中發生。

*pvDest 上下文*<br/>
保留供將來使用;必須為 NULL。

*毫秒旗標*<br/>
指示要封送的數據是傳輸回用戶端進程(典型情況)還是寫入全域表(多個用戶端可以檢索)的標誌。 指定一個或多個 MSHLFLAGS 枚舉值。

*pSize*<br/>
此操作完成後,指標指向要寫入封送流的數據量上的上限。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_FAIL或E_NOINTERFACE。

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase:取得 Unmarshal 類

取得 COM 用於查找包含相應代理程式碼的 DLL 的 CLSID。 COM 載入此 DLL 以建立代理的未初始化實體。

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>參數

*riid*<br/>
對要封送的介面的標識符的引用。

*光伏*<br/>
指向要封送的介面的指標;如果呼叫方沒有指向所需介面的指標,則可以為 NULL。

*dwDest 上下文*<br/>
要取消封送指定介面的目標上下文。

指定一個或多個 MSHCTX 枚舉值。

取消封送可以在當前進程的另一個單元(MSHCTX_INPROC)中,也可以與當前進程 (MSHCTX_LOCAL) 在同一台計算機上的另一個進程中發生解封送。

*pvDest 上下文*<br/>
保留供將來使用;必須為 NULL。

*毫秒旗標*<br/>
此操作完成後,指向 CLSID 的指標將用於在用戶端進程中創建代理。

*pCid*

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,S_FALSE。

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase::MarshalInterface

將在某些用戶端進程中初始化代理物件所需的數據寫入流中。

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>參數

*pStm*<br/>
指向在封送過程中使用的流的指標。

*riid*<br/>
對要封送的介面的標識符的引用。 此介面必須衍生自 `IUnknown` 介面。

*光伏*<br/>
指向要封送的介面指標;如果呼叫方沒有指向所需介面的指標,則可以為 NULL。

*dwDest 上下文*<br/>
要取消封送指定介面的目標上下文。

指定一個或多個 MSHCTX 枚舉值。

取消封送可以發生在當前進程的另一個單元(MSHCTX_INPROC),也可以與當前進程 (MSHCTX_LOCAL) 在同一台計算機上的另一個進程中發生。

*pvDest 上下文*<br/>
保留以備將來之用；必須為零。

*毫秒旗標*<br/>
指定要封送的數據是要傳輸回用戶端進程(典型情況),還是寫入全域表,由多個用戶端檢索這些數據。

### <a name="return-value"></a>傳回值

S_OK介面指標已成功封送。

E_NOINTERFACE不支援指定的介面。

STG_E_MEDIUMFULL流已滿。

E_FAIL 操作失敗。

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>FtmBase:marshaller_

保存對自由線程封送器的引用。

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase::釋放元帥數據

銷毀封送的數據包。

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>參數

*pStm*<br/>
指向包含要銷毀的數據包的流的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase:取消封送介面

初始化新創建的代理並返回指向該代理的介面指標。

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>參數

*pStm*<br/>
指向要取消封送介面指標的流。

*riid*<br/>
引用要取消封送的介面的標識符。

*Ppv*<br/>
此操作完成後,接收*riid*中請求的介面指標的指標變數的位址。 如果此操作成功,**ppv*包含要取消封解的介面的請求介面指標。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_NOINTERFACE或E_FAIL。
