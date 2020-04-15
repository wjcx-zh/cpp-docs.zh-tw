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
ms.openlocfilehash: 5548bee36ac52dbd6add31241714b0404289be45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319187"
---
# <a name="atl-typedefs"></a>ATL Typedef

活動範本庫包括以下類型定義。

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|定義為基於[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)的 typedef。|
|[_ATL_COM_MODULE](#_atl_com_module)|定義為基於[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)的類型定義。|
|[_ATL_MODULE](#_atl_module)|定義為基於[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)的類型定義。|
|[_ATL_WIN_MODULE](#_atl_win_module)|定義為基於[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)的類型定義|
|[ATL_URL_PORT](#atl_url_port)|[CUrl](../../atl/reference/curl-class.md)用於指定埠號的類型。|
|[CCom排程驅動程式](#ccomdispatchdriver)|此類管理 COM 介面指標。|
|[CComGlobalsThread模型](#ccomglobalsthreadmodel)|調用適當的線程模型方法,而不考慮使用的線程模型。|
|[CComObject 執行緒模型](#ccomobjectthreadmodel)|調用適當的線程模型方法,而不考慮使用的線程模型。|
|[包含視窗](#ccontainedwindow)|此是的專業化課程`CContainedWindowT`。|
|[CPath](#cpath)|使用[的 CPathT](../../atl/reference/cpatht-class.md)的專門`CString`化。|
|[查帕](#cpatha)|使用[的 CPathT](../../atl/reference/cpatht-class.md)的專門`CStringA`化。|
|[CPathW](#cpathw)|使用[的 CPathT](../../atl/reference/cpatht-class.md)的專門`CStringW`化。|
|[CSimpleValarray](#csimplevalarray)|表示用於存儲簡單類型的陣列。|
|[預設執行緒特徵](#defaultthreadtraits)|默認線程特徵類。|
|[LPCURL](#lpcurl)|指向常量[CUrl](../../atl/reference/curl-class.md)物件的指標。|
|[LPURL](#lpurl)|指向[CUrl](../../atl/reference/curl-class.md)物件的指標。|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

定義為基於_ATL_BASE_MODULE70的類型定義。

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>備註

用於每個 ATL 專案。 基於[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。

屬於 ATL 7.0 模組類的類派生自_ATL_BASE_MODULE結構。  有關 ATL 模組類別的詳細資訊,請參考[COM 模組類別](../../atl/com-modules-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

定義為基於_ATL_COM_MODULE70的類型定義。

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>備註

使用 COM 功能的 ATL 專案使用。 基於[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

定義為基於_ATL_MODULE70的類型定義。

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>需求

**頭:**

### <a name="remarks"></a>備註

基於[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

定義為基於_ATL_WIN_MODULE70的類型定義。

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>備註

使用視窗功能的任何 ATL 專案使用。 基於[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

[CUrl](curl-class.md)用於指定埠號的類型。

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CCom排程驅動程式

此類管理 COM 介面指標。

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThread模型

調用適當的線程模型方法,而不考慮使用的線程模型。

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

根據應用程式使用的線程模型 **,typedef**名稱`CComGlobalsThreadModel`引用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 這些類提供用於`typedef`引用關鍵節類的其他名稱。

> [!NOTE]
> `CComGlobalsThreadModel`不參考類別[CCom 多線程式程式NoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComGlobalsThreadModel`可使您從指定特定的線程模型類中釋放。 無論使用哪種線程模型,都將調用適當的方法。

除`CComGlobalsThreadModel`之外 ,ATL 還提供**類型定義**名稱[CComObjectThreadModel](#ccomobjectthreadmodel)。 每個`typedef`類引用的類取決於所使用的線程模型,如下表所示:

|typedef|單線程|公寓線程|免費線程|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

在`CComObjectThreadModel`單個物件類中使用。 在`CComGlobalsThreadModel`程式全域可用的物件中使用,或者當您希望跨多個線程保護模組資源時。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObject 執行緒模型

調用適當的線程模型方法,而不考慮使用的線程模型。

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

根據應用程式使用的線程模型`typedef`,`CComObjectThreadModel`名稱引用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 這些類提供用於`typedef`引用關鍵節類的其他名稱。

> [!NOTE]
> `CComObjectThreadModel`不參考類別[CCom 多線程式程式NoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComObjectThreadModel`可使您從指定特定的線程模型類中釋放。 無論使用哪種線程模型,都將調用適當的方法。

除`CComObjectThreadModel`之外 ,ATL 還提供**類型定義**名稱[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 每個**typedef**引用的類別取決於所使用的線程模型,如下表所示:

|typedef|單線程|公寓線程|免費線程|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

在`CComObjectThreadModel`單個物件類中使用。 在`CComGlobalsThreadModel`程式全域可用的物件中,或者當您希望跨多個線程保護模組資源時,請使用該物件。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>包含視窗

此是的專業化課程`CContainedWindowT`。

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>需求

**標題:** atlwin.h

### <a name="remarks"></a>備註

`CContainedWindow`是[CContainedWindowT 的](../../atl/reference/ccontainedwindowt-class.md)專業化。 如果要變更基類別或特徵,請使用`CContainedWindowT`。

## <a name="cpath"></a><a name="cpath"></a>CPath

使用[的 CPathT](../../atl/reference/cpatht-class.md)的專門`CString`化。

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>需求

**標題:** atlpath.h

## <a name="cpatha"></a><a name="cpatha"></a>查帕

使用[的 CPathT](../../atl/reference/cpatht-class.md)的專門`CStringA`化。

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>需求

**標題:** atlpath.h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

使用[的 CPathT](../../atl/reference/cpatht-class.md)的專門`CStringW`化。

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>需求

**標題:** atlpath.h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValarray

表示用於存儲簡單類型的陣列。

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>備註

`CSimpleValArray`用於建立和管理包含簡單資料類型的陣列。 這是[一個簡單的#defineCSimplearray。](../../atl/reference/csimplearray-class.md)

## <a name="requirements"></a>需求

**標題:** atlsimpcoll.h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

指向常量[CUrl](../../atl/reference/curl-class.md)物件的指標。

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>預設執行緒特徵

默認線程特徵類。

### <a name="syntax"></a>語法

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>備註

如果目前專案使用多線程 CRT,則預設線程特徵定義為 CRTThreadTraits。 否則,使用 Win32ThreadTraits。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

指向[CUrl](../../atl/reference/curl-class.md)物件的指標。

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[函式](../../atl/reference/atl-functions.md)<br/>
[全域變數](../../atl/reference/atl-global-variables.md)<br/>
[類別和結構](../../atl/reference/atl-classes.md)<br/>
[巨集](../../atl/reference/atl-macros.md)
