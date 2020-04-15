---
title: IRegistrar 介面
ms.date: 02/01/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 98943fe294322715723bd91207a6f3320ca1ffb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329456"
---
# <a name="iregistrar-interface"></a>IRegistrar 介面

此介面在 atliface.h 中定義,並由 CAtlModule 成員函數(如[UpdateRegistry FromResourceD)](catlmodule-class.md#updateregistryfromresourced)在內部使用。

## <a name="syntax"></a>語法

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>備註

有關詳細資訊,請參閱["使用可替換參數(註冊器的預處理器)"](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)主題。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I註冊商::資源註冊](#resourceregistersz)|註冊資源。 |
|[I註冊人::資源未註冊](#resourceunregistersz)| 取消註冊資源。|
|[I註冊人:檔案註冊](#fileregister)|註冊檔。|
|[I註冊人::檔未註冊](#fileunregister)|取消註冊該檔。|
|[IRegistrar::字串註冊](#stringregister)|註冊字串。|
|[I註冊人::字串未註冊](#stringunregister)|取消註冊字串|
|[I註冊人::資源註冊](#resourceregister)|註冊資源。|
|[I註冊人::資源未註冊](#resourceunregister)|取消註冊資源。|

## <a name="requirements"></a>需求

**標題:** atlifase.h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a>I註冊商::資源註冊

註冊資源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a>I註冊人::資源未註冊

取消註冊資源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a>I註冊人:檔案註冊

註冊檔。

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a>I註冊人::檔未註冊

取消註冊該檔。

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a>IRegistrar::字串註冊

註冊指定的字串資料。

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a>I註冊人::字串未註冊

取消註冊指定的字串資料。

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a>I註冊人::資源註冊

註冊資源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a>I註冊人::資源未註冊

取消註冊資源。

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>另請參閱

[使用可取代參數(註冊商的預處理器)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類](../../atl/atl-module-classes.md)<br/>
[登錄元件 (登錄器)](../../atl/atl-registry-component-registrar.md)
