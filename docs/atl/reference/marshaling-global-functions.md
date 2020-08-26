---
title: 封送處理全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: 79b19b613fbae49c0f8338dcadd2225e092fb371
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835320"
---
# <a name="marshaling-global-functions"></a>封送處理全域函式

這些函式可支援封送處理和將封送處理資料轉換成介面指標。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|名稱|描述|
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|釋放封送處理資料和 `IStream` 指標。|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|建立新的資料流程物件，並將指定的介面指標封送處理。|
|[AtlUnmarshalPtr](#atlunmarshalptr)|將資料流程的封送處理資料轉換成介面指標。|

## <a name="requirements"></a>需求：

**標頭：** atlbase.h。h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a> AtlFreeMarshalStream

釋放資料流的封送處理資料，然後釋放資料流指標。

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
在 `IStream` 資料流程上用來進行封送處理之介面的指標。

### <a name="example"></a>範例

請參閱 [AtlMarshalPtrInProc](#atlmarshalptrinproc)的範例。

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a> AtlMarshalPtrInProc

建立新的資料流物件、將 Proxy 的 CLSID 寫入資料流，並且藉由將初始化 Proxy 所需的資料寫入資料流的方式封送處理指定的介面指標。

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>參數

*朋 克*<br/>
在要封送處理之介面的指標。

*Iid*<br/>
在要封送處理之介面的 GUID。

*ppStream*<br/>
擴展 `IStream` 新資料流程物件上用來封送處理的介面指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

已設定 MSHLFLAGS_TABLESTRONG 旗標，因此可以將指標封送處理至多個資料流程。 指標也可以多次進行封送。

如果封送處理失敗，則會釋放資料流程指標。

`AtlMarshalPtrInProc` 只能用在同進程物件的指標上。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a> AtlUnmarshalPtr

將資料流的封送處理資料轉換成可供用戶端使用的介面指標。

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>參數

*pStream*<br/>
在要取消封送的資料流程指標。

*Iid*<br/>
在正在取消封送之介面的 GUID。

*ppUnk*<br/>
擴展取消封送的介面指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

請參閱 [AtlMarshalPtrInProc](#atlmarshalptrinproc)的範例。

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)
