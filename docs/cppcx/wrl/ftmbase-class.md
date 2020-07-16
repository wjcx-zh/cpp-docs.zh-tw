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
ms.openlocfilehash: f28a850c365bc9a75d8e5b100e5e5cc0a1c5dc10
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404560"
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

如需詳細資訊，請參閱[RuntimeClass 類別](runtimeclass-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱                         | 描述                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase：： FtmBase](#ftmbase) | 初始化 `FtmBase` 類別的新執行個體。 |

### <a name="public-methods"></a>公用方法

| 名稱                                                               | 描述                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase：： CreateGlobalInterfaceTable](#createglobalinterfacetable) | 建立全域介面表（GIT）。                                                                                                                              |
| [FtmBase：:D isconnectObject](#disconnectobject)                     | 強制釋放物件的所有外部連接。 物件的伺服器會在關閉之前呼叫這個方法的物件的執行。                |
| [FtmBase：： GetMarshalSizeMax](#getmarshalsizemax)                   | 取得在指定的物件上封送處理指定的介面指標所需的位元組數目上限。                                                |
| [FtmBase：： GetUnmarshalClass](#getunmarshalclass)                   | 取得 CLSID，以供 COM 用來尋找包含對應 proxy 之程式碼的 DLL。 COM 會載入此 DLL，以建立未初始化的 proxy 實例。 |
| [FtmBase：： MarshalInterface](#marshalinterface)                     | 將在某些用戶端進程中初始化 proxy 物件所需的資料寫入資料流程中。                                                                          |
| [FtmBase：： ReleaseMarshalData](#releasemarshaldata)                 | 損毀封送處理的資料封包。                                                                                                                                    |
| [FtmBase：： UnmarshalInterface](#unmarshalinterface)                 | 初始化新建立的 proxy，並將介面指標傳回給該 proxy。                                                                                    |

### <a name="public-data-members"></a>公用資料成員

| 名稱                                | 描述                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase：： marshaller_](#marshaller) | 保留免費執行緒封送處理器的參考。 |

## <a name="inheritance-hierarchy"></a>繼承階層架構

`FtmBase`

## <a name="requirements"></a>需求

**標頭：** ftm。h

**命名空間：** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase：： CreateGlobalInterfaceTable

建立全域介面表（GIT）。

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>參數

*git*<br/>
當此作業完成時，即為全域介面資料表的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [`IGlobalInterfaceTable`](https://docs.microsoft.com/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable)。

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase：:D isconnectObject

強制釋放物件的所有外部連接。 物件的伺服器會在關閉之前呼叫這個方法的物件的執行。

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>參數

*dwReserved*<br/>
保留以備將來之用；必須為零。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>FtmBase：： FtmBase

初始化 `FtmBase` 類別的新執行個體。

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase：： GetMarshalSizeMax

取得在指定的物件上封送處理指定的介面指標所需的位元組數目上限。

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
要封送處理之介面的識別碼參考。

*pv*<br/>
要封送處理的介面指標;可以是 Null。

*dwDestCoNtext*<br/>
要解除封送的指定介面所在的目的地內容。

指定一或多個 MSHCTX 列舉值。

目前，可能會在目前進程的另一個單元中（MSHCTX_INPROC），或在與目前進程（MSHCTX_LOCAL）相同電腦上的另一個進程中，進行取消封送處理。

*pvDestCoNtext*<br/>
保留供日後使用;必須是 Null。

*mshlflags*<br/>
旗標，指出要封送處理的資料是否要傳送回用戶端進程（一般情況），或寫入至全域資料表，供多個用戶端抓取。 指定一或多個 MSHLFLAGS 列舉值。

*pSize*<br/>
當此作業完成時，即為要寫入封送處理資料流程之資料量上限的指標。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_FAIL 或 E_NOINTERFACE。

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase：： GetUnmarshalClass

取得 CLSID，以供 COM 用來尋找包含對應 proxy 之程式碼的 DLL。 COM 會載入此 DLL，以建立未初始化的 proxy 實例。

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
要封送處理之介面的識別碼參考。

*pv*<br/>
要封送處理之介面的指標;如果呼叫端沒有所需介面的指標，則可以是 Null。

*dwDestCoNtext*<br/>
要解除封送的指定介面所在的目的地內容。

指定一或多個 MSHCTX 列舉值。

在目前進程的另一個單元中（MSHCTX_INPROC），或在與目前進程（MSHCTX_LOCAL）相同電腦上的另一個進程中，可能會發生封送處理。

*pvDestCoNtext*<br/>
保留供日後使用;必須是 Null。

*mshlflags*<br/>
當此作業完成時，指向要用來在用戶端進程中建立 proxy 的 CLSID 的指標。

*pCid*

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，S_FALSE。

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase：： MarshalInterface

將在某些用戶端進程中初始化 proxy 物件所需的資料寫入資料流程中。

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
封送處理期間所要使用之資料流程的指標。

*riid*<br/>
要封送處理之介面的識別碼參考。 此介面必須衍生自 `IUnknown` 介面。

*pv*<br/>
要封送處理之介面指標的指標;如果呼叫端沒有所需介面的指標，則可以是 Null。

*dwDestCoNtext*<br/>
要解除封送的指定介面所在的目的地內容。

指定一或多個 MSHCTX 列舉值。

在目前進程的另一個單元中（MSHCTX_INPROC），或在與目前進程（MSHCTX_LOCAL）相同電腦上的另一個進程中，可能會發生封送處理。

*pvDestCoNtext*<br/>
保留以備將來之用；必須為零。

*mshlflags*<br/>
指定要封送處理的資料是否要傳送回用戶端進程（一般情況），或寫入至全域資料表，供多個用戶端抓取。

### <a name="return-value"></a>傳回值

已成功封送處理介面指標 S_OK。

不支援指定的介面 E_NOINTERFACE。

STG_E_MEDIUMFULL 資料流程已滿。

E_FAIL 操作失敗。

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>FtmBase：： marshaller_

保留免費執行緒封送處理器的參考。

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase：： ReleaseMarshalData

損毀封送處理的資料封包。

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>參數

*pStm*<br/>
資料流程的指標，其中包含要終結的資料封包。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase：： UnmarshalInterface

初始化新建立的 proxy，並將介面指標傳回給該 proxy。

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>參數

*pStm*<br/>
要解除封送之介面指標所在的資料流程指標。

*riid*<br/>
要解除封送的介面之識別碼的參考。

*ppv*<br/>
當此作業完成時，會接收在*riid*中要求之介面指標的指標變數位址。 如果這項作業成功，**ppv*會包含要解除封送的介面所要求的介面指標。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_NOINTERFACE 或 E_FAIL。
