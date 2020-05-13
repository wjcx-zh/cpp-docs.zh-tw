---
title: 封送全域函數
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: b839e93b6251a09ce79df60a49b4054d1af76cc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326270"
---
# <a name="marshaling-global-functions"></a>封送全域函數

這些函數支援將封送數據進行封送和轉換到介面指標中。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|釋放封送數據和`IStream`指標。|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|創建新的流物件並封送指定的介面指標。|
|[AtlUnmarshalPtr](#atlunmarshalptr)|將流的封送數據轉換為介面指標。|

## <a name="requirements"></a>需求：

**標題:** atlbase.h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream

釋放資料流的封送處理資料，然後釋放資料流指標。

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
[在]指向用於封送`IStream`的流上的介面的指標。

### <a name="example"></a>範例

請參閱[AtlMarshalPtrInProc](#atlmarshalptrinproc)的範例。

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrinProc

建立新的資料流物件、將 Proxy 的 CLSID 寫入資料流，並且藉由將初始化 Proxy 所需的資料寫入資料流的方式封送處理指定的介面指標。

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]指向要封送的介面的指標。

*Iid*<br/>
[在]正在封送的介面的 GUID。

*ppStream*<br/>
[出]指向用於封送`IStream`的新流物件上的介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

設置MSHLFLAGS_TABLESTRONG標誌,以便可以將指標封送到多個流。 指標也可以多次取消封解。

如果封送失敗,將釋放流指標。

`AtlMarshalPtrInProc`只能在指向進程內物件的指標上使用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr

將資料流的封送處理資料轉換成可供用戶端使用的介面指標。

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>參數

*pStream*<br/>
[在]指向未封解的流的指標。

*Iid*<br/>
[在]未封送介面的 GUID。

*普恩克*<br/>
[出]指向未封解介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

請參閱[AtlMarshalPtrInProc](#atlmarshalptrinproc)的範例。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
