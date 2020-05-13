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
ms.openlocfilehash: 26e4e80ed3110351130731e6030427d25fc4a0ea
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168731"
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
|[CContainedWindow](#ccontainedwindow)|這個類別是的特製化`CContainedWindowT`。|
|[CPath](#cpath)|使用`CString` [CPathT](../../atl/reference/cpatht-class.md)的特製化。|
|[CPathA](#cpatha)|使用`CStringA` [CPathT](../../atl/reference/cpatht-class.md)的特製化。|
|[CPathW](#cpathw)|使用`CStringW` [CPathT](../../atl/reference/cpatht-class.md)的特製化。|
|[CSimpleValArray](#csimplevalarray)|表示用於儲存簡單類型的陣列。|
|[DefaultThreadTraits](#defaultthreadtraits)|預設執行緒特性類別。|
|[LPCURL](#lpcurl)|常數[捲曲](../../atl/reference/curl-class.md)物件的指標。|
|[LPURL](#lpurl)|[捲曲](../../atl/reference/curl-class.md)物件的指標。|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

定義為以 _ATL_BASE_MODULE70 為基礎的 typedef。

```cpp
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>備註

用於每個 ATL 專案。 根據[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。

屬於 ATL 7.0 模組類別之一部分的類別，衍生自 _ATL_BASE_MODULE 結構。  如需 ATL 模組類別的詳細資訊，請參閱[COM 模組類別](../../atl/com-modules-classes.md)。

### <a name="requirements"></a>需求

**標頭：** atlcore。h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

定義為以 _ATL_COM_MODULE70 為基礎的 typedef。

```cpp
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>備註

由使用 COM 功能的 ATL 專案所使用。 根據[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

定義為以 _ATL_MODULE70 為基礎的 typedef。

```cpp
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

### <a name="requirements"></a>需求

**標頭**

### <a name="remarks"></a>備註

根據[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

定義為以 _ATL_WIN_MODULE70 為基礎的 typedef。

```cpp
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>備註

由任何使用視窗化功能的 ATL 專案所使用。 根據[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

由[捲曲](curl-class.md)用來指定埠號碼的類型。

```cpp
typedef WORD ATL_URL_PORT;
```

### <a name="requirements"></a>需求

**標頭：** atlutil。h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

這個類別會管理 COM 介面指標。

```cpp
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

不論使用的執行緒模型為何，都會呼叫適當的執行緒模型方法。

```cpp
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

根據您的應用程式所使用的執行緒模型， **typedef**名稱`CComGlobalsThreadModel`會參考[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 這些類別會提供`typedef`參考重要區段類別的其他名稱。

> [!NOTE]
> `CComGlobalsThreadModel`未參考類別[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComGlobalsThreadModel`可讓您指定特定的執行緒模型類別。 不論使用的執行緒模型為何，將會呼叫適當的方法。

除了之外`CComGlobalsThreadModel`，ATL 還提供**typedef**名稱[CComObjectThreadModel](#ccomobjectthreadmodel)。 每個所參考的`typedef`類別都取決於所使用的執行緒模型，如下表所示：

|typedef|單一線程|單元執行緒|自由執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M =`CComMultiThreadModel`

在`CComObjectThreadModel`單一物件類別中使用。 使用`CComGlobalsThreadModel`于全域可用的物件中，或當您想要跨多個執行緒保護模組資源時。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

不論使用的執行緒模型為何，都會呼叫適當的執行緒模型方法。

```cpp
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

根據您的應用程式所使用的執行緒模型， `typedef`名稱`CComObjectThreadModel`會參考[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 這些類別會提供`typedef`參考重要區段類別的其他名稱。

> [!NOTE]
> `CComObjectThreadModel`未參考類別[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComObjectThreadModel`可讓您指定特定的執行緒模型類別。 不論使用的執行緒模型為何，將會呼叫適當的方法。

除了之外`CComObjectThreadModel`，ATL 還提供**typedef**名稱[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 每個**typedef**所參考的類別取決於所使用的執行緒模型，如下表所示：

|typedef|單一線程|單元執行緒|自由執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M =`CComMultiThreadModel`

在`CComObjectThreadModel`單一物件類別中使用。 在`CComGlobalsThreadModel`可全域提供給您的程式的物件中使用，或當您想要跨多個執行緒保護模組資源時使用。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

這個類別是的特製化`CContainedWindowT`。

```cpp
typedef CContainedWindowT<CWindow> CContainedWindow;
```

### <a name="requirements"></a>需求

**標頭：** atlwin.h。h

### <a name="remarks"></a>備註

`CContainedWindow`是[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)的特製化。 如果您想要變更基類或特性，請直接使用`CContainedWindowT` 。

## <a name="cpath"></a><a name="cpath"></a>CPath

使用`CString` [CPathT](../../atl/reference/cpatht-class.md)的特製化。

```cpp
typedef CPathT<CString> CPath;
```

### <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA

使用`CStringA` [CPathT](../../atl/reference/cpatht-class.md)的特製化。

```cpp
typedef CPathT<CStringA> CPathA;
```

### <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

使用`CStringW` [CPathT](../../atl/reference/cpatht-class.md)的特製化。

```cpp
typedef ATL::CPathT<CStringW> CPathW;
```

### <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

表示用於儲存簡單類型的陣列。

```cpp
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>備註

`CSimpleValArray`提供來建立和管理包含單一資料型別的陣列。 這是[CSimpleArray](../../atl/reference/csimplearray-class.md)的簡單 #define。

### <a name="requirements"></a>需求

**標頭：** atlsimpcoll。h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

常數[捲曲](../../atl/reference/curl-class.md)物件的指標。

```cpp
typedef const CUrl* LPCURL;
```

### <a name="requirements"></a>需求

**標頭：** atlutil。h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DefaultThreadTraits

預設執行緒特性類別。

### <a name="syntax"></a>語法

```cpp
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>備註

如果目前的專案使用多執行緒 CRT，則 DefaultThreadTraits 會定義為 CRTThreadTraits。 否則，會使用 Win32ThreadTraits。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

[捲曲](../../atl/reference/curl-class.md)物件的指標。

```cpp
typedef CUrl* LPURL;
```

### <a name="requirements"></a>需求

**標頭：** atlutil。h

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[函式](../../atl/reference/atl-functions.md)<br/>
[全域變數](../../atl/reference/atl-global-variables.md)<br/>
[類別和結構](../../atl/reference/atl-classes.md)<br/>
[巨集](../../atl/reference/atl-macros.md)
