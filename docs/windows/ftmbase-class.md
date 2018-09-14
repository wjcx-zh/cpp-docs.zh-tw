---
title: FtmBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 687fd4f4bd77043bd0b74c7bcc39fb6a496b60be
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601453"
---
# <a name="ftmbase-class"></a>FtmBase 類別

代表無限制執行緒封送處理器物件。

## <a name="syntax"></a>語法

```cpp
class FtmBase : public Microsoft::WRL::Implements<
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
   Microsoft::WRL::CloakedIid<IMarshal> >;
```

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [RuntimeClass 類別](runtimeclass-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱                         | 描述                                        |
| ---------------------------- | -------------------------------------------------- |
| [Ftmbase:: Ftmbase](#ftmbase) | 初始化 `FtmBase` 類別的新執行個體。 |

### <a name="public-methods"></a>公用方法

| 名稱                                                               | 描述                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Ftmbase:: Createglobalinterfacetable](#createglobalinterfacetable) | 建立全域介面表 (GIT)。                                                                                                                              |
| [Ftmbase:: Disconnectobject](#disconnectobject)                     | 強制釋放物件的所有外部連線。 物件的伺服器會呼叫這個方法之前關閉物件的實作。                |
| [Ftmbase:: Getmarshalsizemax](#getmarshalsizemax)                   | 取得指定的物件上指定的介面指標封送處理所需的位元組數目上限。                                                |
| [Ftmbase:: Getunmarshalclass](#getunmarshalclass)                   | 取得 COM 使用，找出包含對應的 proxy 程式碼的 DLL 的 CLSID。 COM 會載入此 DLL 來建立未初始化的執行個體的 proxy。 |
| [Ftmbase:: Marshalinterface](#marshalinterface)                     | 寫入資料流來初始化 proxy 物件中某些用戶端處理序所需的資料。                                                                          |
| [Ftmbase:: Releasemarshaldata](#releasemarshaldata)                 | 終結封送處理的資料封包。                                                                                                                                    |
| [Ftmbase:: Unmarshalinterface](#unmarshalinterface)                 | 初始化新建立的 proxy，並將該 proxy 傳回的介面指標。                                                                                    |

### <a name="public-data-members"></a>公用資料成員

| 名稱                                | 描述                                       |
| ----------------------------------- | ------------------------------------------------- |
| [Ftmbase:: Marshaller_](#marshaller) | 保留無限制執行緒封送處理器的參考。 |

## <a name="inheritance-hierarchy"></a>繼承階層

`FtmBase`

## <a name="requirements"></a>需求

**標頭：** ftm.h

**命名空間：** Microsoft::WRL

## <a name="createglobalinterfacetable"></a>Ftmbase:: Createglobalinterfacetable

建立全域介面表 (GIT)。

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>參數

*Git*  
這項作業完成時，全域介面表的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> `IGlobalInterfaceTable` 中的主題`COM Interfaces`的子主題`COM Reference`MSDN Library 中的主題。

## <a name="disconnectobject"></a>Ftmbase:: Disconnectobject

強制釋放物件的所有外部連線。 物件的伺服器會呼叫這個方法之前關閉物件的實作。

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>參數

*dwReserved*  
保留以備將來之用；必須為零。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="ftmbase"></a>Ftmbase:: Ftmbase

初始化 `FtmBase` 類別的新執行個體。

```cpp
FtmBase();
```

## <a name="getmarshalsizemax"></a>Ftmbase:: Getmarshalsizemax

取得指定的物件上指定的介面指標封送處理所需的位元組數目上限。

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

*riid*  
要封送處理介面識別項參考。

*pv*  
要封送處理; 介面指標可以是 NULL。

*dwDestContext*  
指定的介面所在解除封送處理的目的端內容。

指定一或多個 MSHCTX 列舉值。

目前，解封送處理可能會發生在另一個 apartment，目前的處理序 (MSHCTX_INPROC) 或在目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序中。

*pvDestContext*  
保留供未來使用;必須是 NULL。

*mshlflags*  
旗標，指出要封送處理的資料是否要傳送回用戶端程序 — 一般的情況下，或寫入全域的資料表，其中要擷取多個用戶端。 指定一或多個 MSHLFLAGS 列舉值。

*pSize*  
這項作業完成時，指標要封送處理的資料流寫入的資料量上限。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_FAIL 或 E_NOINTERFACE。

## <a name="getunmarshalclass"></a>Ftmbase:: Getunmarshalclass

取得 COM 使用，找出包含對應的 proxy 程式碼的 DLL 的 CLSID。 COM 會載入此 DLL 來建立未初始化的執行個體的 proxy。

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

*riid*  
要封送處理介面識別項參考。

*pv*  
要封送處理; 介面指標如果呼叫端所需的介面沒有指標，則可以是 NULL。

*dwDestContext*  
指定的介面所在解除封送處理的目的端內容。

指定一或多個 MSHCTX 列舉值。

解封送處理，可能會發生在目前的處理序 (MSHCTX_INPROC) 的另一個 apartment，或在目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序。

*pvDestContext*  
保留供未來使用;必須是 NULL。

*mshlflags*  
這項作業完成時，用來在用戶端處理序中建立 proxy 的 CLSID 指標。

*pCid*

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，S_FALSE。

## <a name="marshalinterface"></a>Ftmbase:: Marshalinterface

寫入資料流來初始化 proxy 物件中某些用戶端處理序所需的資料。

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

*pStm*  
要封送處理期間使用的資料流的指標。

*riid*  
要封送處理介面識別項參考。 此介面必須衍生自`IUnknown`介面。

*pv*  
要封送處理; 之介面指標的指標如果呼叫端所需的介面沒有指標，則可以是 NULL。

*dwDestContext*  
指定的介面所在解除封送處理的目的端內容。

指定一或多個 MSHCTX 列舉值。

解封送處理，可能會發生在目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序或目前的處理序 (MSHCTX_INPROC) 的另一個 apartment 中。

*pvDestContext*  
保留以備將來之用；必須為零。

*mshlflags*  
指定要封送處理的資料是否要傳送回用戶端程序 — 一般的情況下，或寫入全域的資料表，其中要擷取多個用戶端。

### <a name="return-value"></a>傳回值

介面指標封送處理成功地傳回 S_OK。

E_NOINTERFACE 不支援指定的介面。

STG_E_MEDIUMFULL 資料流已滿。

E_FAIL 作業失敗。

## <a name="marshaller"></a>Ftmbase:: Marshaller_

保留無限制執行緒封送處理器的參考。

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="releasemarshaldata"></a>Ftmbase:: Releasemarshaldata

終結封送處理的資料封包。

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>參數

*pStm*  
包含資料封包，也將被銷毀的資料流的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="unmarshalinterface"></a>Ftmbase:: Unmarshalinterface

初始化新建立的 proxy，並將該 proxy 傳回的介面指標。

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>參數

*pStm*  
從中的介面指標是解除封送處理的資料流的指標。

*riid*  
要解除封送處理介面識別項參考。

*ppv*  
這項作業完成時，接收所要求的介面指標的指標變數的位址*riid*。 如果這項作業成功，**ppv*包含要解除封送處理介面的要求的介面指標。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_NOINTERFACE 或 E_FAIL。
