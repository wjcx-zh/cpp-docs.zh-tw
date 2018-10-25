---
title: ATL Typedef |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
dev_langs:
- C++
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9835b8cadb5a24aea130b1e32d919ebb49d20293
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065690"
---
# <a name="atl-typedefs"></a>ATL Typedef

Active Template Library 包含下列的 typedef。

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|定義為根據的 typedef [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。|
|[_ATL_COM_MODULE](#_atl_com_module)|定義為根據的 typedef [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。|
|[_ATL_MODULE](#_atl_module)|定義為根據的 typedef [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。|
|[_ATL_WIN_MODULE](#_atl_win_module)|定義為根據的 typedef [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|所使用的類型[CUrl](../../atl/reference/curl-class.md)來指定連接埠號碼。|
|[CComDispatchDriver](#ccomdispatchdriver)|此類別會管理 COM 介面指標。|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|呼叫適當的執行緒模型的方法，不論所使用的執行緒模型。|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|呼叫適當的執行緒模型的方法，不論所使用的執行緒模型。|
|[CContainedWindow](#ccontainedwindow)|這個類別是特製化的`CContainedWindowT`。|
|[CPath](#cpath)|特製化[CPathT](../../atl/reference/cpatht-class.md)使用`CString`。|
|[CPathA](#cpatha)|特製化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringA`。|
|[CPathW](#cpathw)|特製化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringW`。|
|[CSimpleValArray](#csimplevalarray)|表示陣列來儲存簡單類型。|
|[DefaultThreadTraits](#defaultthreadtraits)|預設執行緒 traits 類別。|
|[LPCURL](#lpcurl)|常數的指標[CUrl](../../atl/reference/curl-class.md)物件。|
|[LPURL](#lpurl)|指標[CUrl](../../atl/reference/curl-class.md)物件。|

##  <a name="_atl_base_module"></a>  _ATL_BASE_MODULE

定義根據 _ATL_BASE_MODULE70 的 typedef。

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>備註

每個 ATL 專案中使用。 根據[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。

ATL 7.0 模組類別一部分的類別衍生自 _ATL_BASE_MODULE 結構。  如需有關 ATL 模組類別的詳細資訊，請參閱[COM 模組類別](../../atl/com-modules-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcore.h

##  <a name="_atl_com_module"></a>  _ATL_COM_MODULE

定義根據 _ATL_COM_MODULE70 的 typedef。

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>備註

使用 ATL 專案使用 COM 功能。 根據[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="_atl_module"></a>  _ATL_MODULE

定義根據 _ATL_MODULE70 的 typedef。

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>需求

**標頭：**

### <a name="remarks"></a>備註

根據[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。

##  <a name="_atl_win_module"></a>  _ATL_WIN_MODULE

定義根據 _ATL_WIN_MODULE70 的 typedef。

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>備註

使用任何 ATL 專案使用時間範圍功能。 根據[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atl_url_port"></a>  ATL_URL_PORT

所使用的類型[CUrl](curl-class.md)來指定連接埠號碼。

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>需求

**標頭：** atlutil.h

##  <a name="ccomdispatchdriver"></a>  CComDispatchDriver

此類別會管理 COM 介面指標。

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="ccomglobalsthreadmodel"></a>  CComGlobalsThreadModel

呼叫適當的執行緒模型的方法，不論所使用的執行緒模型。

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>備註

根據您的應用程式所使用的執行緒模型**typedef**名稱`CComGlobalsThreadModel`參照[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). 這些類別提供額外`typedef`參考關鍵區段類別的名稱。

> [!NOTE]
> `CComGlobalsThreadModel` 未參考類別[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComGlobalsThreadModel`讓您指定特定的執行緒模型類別。 不論所使用的執行緒模型，就會呼叫適當的方法。

除了`CComGlobalsThreadModel`，提供 ATL **typedef**名稱[CComObjectThreadModel](#ccomobjectthreadmodel)。 每個參考的類別`typedef`取決於執行緒模型，如下表所示：

|typedef|單一執行緒處理|Apartment 執行緒|無限制執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

使用`CComObjectThreadModel`內的單一物件類別。 使用`CComGlobalsThreadModel`中物件的全域可用於您的程式，或想要保護多個執行緒上的模組資源時。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="ccomobjectthreadmodel"></a>  CComObjectThreadModel

呼叫適當的執行緒模型的方法，不論所使用的執行緒模型。

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComObjectThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>備註

根據您的應用程式所使用的執行緒模型`typedef`名稱`CComObjectThreadModel`參照[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或是[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 這些類別提供額外`typedef`參考關鍵區段類別的名稱。

> [!NOTE]
> `CComObjectThreadModel` 未參考類別[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComObjectThreadModel`讓您指定特定的執行緒模型類別。 不論所使用的執行緒模型，就會呼叫適當的方法。

除了`CComObjectThreadModel`，提供 ATL **typedef**名稱[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 每個參考的類別**typedef**取決於執行緒模型，如下表所示：

|typedef|單一執行緒處理|Apartment 執行緒|無限制執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

使用`CComObjectThreadModel`內的單一物件類別。 使用`CComGlobalsThreadModel`物件，是在全球都可使用您的程式，或當您想要保護多個執行緒上的模組資源。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="ccontainedwindow"></a>  CContainedWindow

這個類別是特製化的`CContainedWindowT`。

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>需求

**標頭：** atlwin.h

### <a name="remarks"></a>備註

`CContainedWindow` 是的特製化[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)。 如果您想要變更的基底類別或特性，使用`CContainedWindowT`直接。

##  <a name="cpath"></a>  CPath

特製化[CPathT](../../atl/reference/cpatht-class.md)使用`CString`。

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>需求

**標頭：** atlpath.h

##  <a name="cpatha"></a>  CPathA

特製化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringA`。

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>需求

**標頭：** atlpath.h

##  <a name="cpathw"></a>  CPathW

特製化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringW`。

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>需求

**標頭：** atlpath.h

##  <a name="csimplevalarray"></a>  CSimpleValArray

表示陣列來儲存簡單類型。

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>備註

`CSimpleValArray` 提供用於建立和管理包含簡單的資料類型的陣列。 它是一項簡單 # 的 define [CSimpleArray](../../atl/reference/csimplearray-class.md)。

## <a name="requirements"></a>需求

**標頭：** atlsimpcoll.h

##  <a name="lpcurl"></a>  LPCURL

常數的指標[CUrl](../../atl/reference/curl-class.md)物件。

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>需求

**標頭：** atlutil.h

##  <a name="defaultthreadtraits"></a>  DefaultThreadTraits

預設執行緒 traits 類別。

### <a name="syntax"></a>語法

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>備註

如果目前的專案使用多執行緒的 CRT，則會將 DefaultThreadTraits 定義為 CRTThreadTraits。 否則，會使用 Win32ThreadTraits。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="lpurl"></a>  LPURL

指標[CUrl](../../atl/reference/curl-class.md)物件。

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>需求

**標頭：** atlutil.h

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[函式](../../atl/reference/atl-functions.md)<br/>
[全域變數](../../atl/reference/atl-global-variables.md)<br/>
[類別和結構](../../atl/reference/atl-classes.md)<br/>
[巨集](../../atl/reference/atl-macros.md)
