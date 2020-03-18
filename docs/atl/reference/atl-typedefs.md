---
title: ATL Typedef
ms.date: 11/04/2016
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
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: f3db32e85ea9cba1e946db6259c00c621650e969
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418255"
---
# <a name="atl-typedefs"></a>ATL Typedef

Active Template Library 包含下列 typedef。

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|定義為以[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)為基礎的 typedef。|
|[_ATL_COM_MODULE](#_atl_com_module)|定義為以[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)為基礎的 typedef。|
|[_ATL_MODULE](#_atl_module)|定義為以[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)為基礎的 typedef。|
|[_ATL_WIN_MODULE](#_atl_win_module)|定義為以[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)為基礎的 typedef|
|[ATL_URL_PORT](#atl_url_port)|由[捲曲](../../atl/reference/curl-class.md)用來指定埠號碼的類型。|
|[CComDispatchDriver](#ccomdispatchdriver)|這個類別會管理 COM 介面指標。|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|不論使用的執行緒模型為何，都會呼叫適當的執行緒模型方法。|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|不論使用的執行緒模型為何，都會呼叫適當的執行緒模型方法。|
|[CContainedWindow](#ccontainedwindow)|這個類別是 `CContainedWindowT`的特製化。|
|[CPath](#cpath)|使用 `CString`的特製化[CPathT](../../atl/reference/cpatht-class.md) 。|
|[CPathA](#cpatha)|使用 `CStringA`的特製化[CPathT](../../atl/reference/cpatht-class.md) 。|
|[CPathW](#cpathw)|使用 `CStringW`的特製化[CPathT](../../atl/reference/cpatht-class.md) 。|
|[CSimpleValArray](#csimplevalarray)|表示用於儲存簡單類型的陣列。|
|[DefaultThreadTraits](#defaultthreadtraits)|預設執行緒特性類別。|
|[LPCURL](#lpcurl)|常數[捲曲](../../atl/reference/curl-class.md)物件的指標。|
|[LPURL](#lpurl)|[捲曲](../../atl/reference/curl-class.md)物件的指標。|

##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE

定義為以 _ATL_BASE_MODULE70 為基礎的 typedef。

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>備註

用於每個 ATL 專案。 根據[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。

屬於 ATL 7.0 模組類別之一部分的類別，衍生自 _ATL_BASE_MODULE 結構。  如需 ATL 模組類別的詳細資訊，請參閱[COM 模組類別](../../atl/com-modules-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcore。h

##  <a name="_atl_com_module"></a>_ATL_COM_MODULE

定義為以 _ATL_COM_MODULE70 為基礎的 typedef。

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>備註

由使用 COM 功能的 ATL 專案所使用。 根據[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="_atl_module"></a>_ATL_MODULE

定義為以 _ATL_MODULE70 為基礎的 typedef。

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>需求

**標頭：**

### <a name="remarks"></a>備註

根據[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。

##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE

定義為以 _ATL_WIN_MODULE70 為基礎的 typedef。

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>備註

由任何使用視窗化功能的 ATL 專案所使用。 根據[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="atl_url_port"></a>ATL_URL_PORT

由[捲曲](curl-class.md)用來指定埠號碼的類型。

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>需求

**標頭：** atlutil。h

##  <a name="ccomdispatchdriver"></a>CComDispatchDriver

這個類別會管理 COM 介面指標。

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

不論使用的執行緒模型為何，都會呼叫適當的執行緒模型方法。

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

根據您的應用程式所使用的執行緒模型， **typedef**名稱 `CComGlobalsThreadModel` 參考[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 這些類別會提供額外的 `typedef` 名稱，以參考重要的區段類別。

> [!NOTE]
> `CComGlobalsThreadModel` 不會參考[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)類別。

使用 `CComGlobalsThreadModel` 可讓您指定特定的執行緒模型類別。 不論使用的執行緒模型為何，將會呼叫適當的方法。

除了 `CComGlobalsThreadModel`以外，ATL 還提供**typedef**名稱[CComObjectThreadModel](#ccomobjectthreadmodel)。 每個 `typedef` 所參考的類別取決於所使用的執行緒模型，如下表所示：

|typedef|單一線程|單元執行緒|自由執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

在單一物件類別中使用 `CComObjectThreadModel`。 在可供您的程式使用的物件中，或當您想要跨多個執行緒保護模組資源時，請使用 `CComGlobalsThreadModel`。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

不論使用的執行緒模型為何，都會呼叫適當的執行緒模型方法。

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

根據您的應用程式所使用的執行緒模型，`typedef` 名稱 `CComObjectThreadModel` 會參考[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 這些類別會提供額外的 `typedef` 名稱，以參考重要的區段類別。

> [!NOTE]
> `CComObjectThreadModel` 不會參考[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)類別。

使用 `CComObjectThreadModel` 可讓您指定特定的執行緒模型類別。 不論使用的執行緒模型為何，將會呼叫適當的方法。

除了 `CComObjectThreadModel`以外，ATL 還提供**typedef**名稱[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 每個**typedef**所參考的類別取決於所使用的執行緒模型，如下表所示：

|typedef|單一線程|單元執行緒|自由執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

在單一物件類別中使用 `CComObjectThreadModel`。 在可供您的程式使用的物件中，或當您想要跨多個執行緒保護模組資源時，請使用 `CComGlobalsThreadModel`。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="ccontainedwindow"></a>CContainedWindow

這個類別是 `CContainedWindowT`的特製化。

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>需求

**標頭：** atlwin.h。h

### <a name="remarks"></a>備註

`CContainedWindow` 是[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)的特製化。 如果您想要變更基類或特性，請直接使用 `CContainedWindowT`。

##  <a name="cpath"></a>CPath

使用 `CString`的特製化[CPathT](../../atl/reference/cpatht-class.md) 。

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

##  <a name="cpatha"></a>CPathA

使用 `CStringA`的特製化[CPathT](../../atl/reference/cpatht-class.md) 。

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

##  <a name="cpathw"></a>CPathW

使用 `CStringW`的特製化[CPathT](../../atl/reference/cpatht-class.md) 。

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

##  <a name="csimplevalarray"></a>CSimpleValArray

表示用於儲存簡單類型的陣列。

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>備註

`CSimpleValArray` 提供來建立和管理包含單一資料型別的陣列。 這是[CSimpleArray](../../atl/reference/csimplearray-class.md)的簡單 #define。

## <a name="requirements"></a>需求

**標頭：** atlsimpcoll。h

##  <a name="lpcurl"></a>LPCURL

常數[捲曲](../../atl/reference/curl-class.md)物件的指標。

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>需求

**標頭：** atlutil。h

##  <a name="defaultthreadtraits"></a>DefaultThreadTraits

預設執行緒特性類別。

### <a name="syntax"></a>語法

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>備註

如果目前的專案使用多執行緒 CRT，則 DefaultThreadTraits 會定義為 CRTThreadTraits。 否則，會使用 Win32ThreadTraits。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="lpurl"></a>LPURL

[捲曲](../../atl/reference/curl-class.md)物件的指標。

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>需求

**標頭：** atlutil。h

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[函數](../../atl/reference/atl-functions.md)<br/>
[全域變數](../../atl/reference/atl-global-variables.md)<br/>
[類別和結構](../../atl/reference/atl-classes.md)<br/>
[巨集](../../atl/reference/atl-macros.md)
