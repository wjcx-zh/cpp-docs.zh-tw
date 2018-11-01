---
title: CreatorMap 結構
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 98afce8096ee514fc8576bb80074b73acdd658e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582438"
---
# <a name="creatormap-structure"></a>CreatorMap 結構

支援的 Windows 執行階段 c + + 樣板程式庫基礎結構，並不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>備註

包含如何初始化、 註冊和取消註冊物件的相關資訊。

`CreatorMap`包含下列資訊：

- 如何初始化、 註冊和取消註冊的物件。

- 比較傳統的 COM 或 Windows 執行階段 factory 根據啟用資料的方式。

- 介面的處理站快取和伺服器名稱的相關資訊。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

名稱                                          | 描述
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[Creatormap:: Activationid](#activationid)     | 表示透過傳統的 COM 類別識別碼或 Windows 執行階段名稱識別的物件識別碼。
[Creatormap:: Factorycache](#factorycache)     | 儲存的處理站快取指標`CreatorMap`。
[Creatormap:: Factorycreator](#factorycreator) | 建立指定的 factory `CreatorMap`。
[Creatormap:: Servername](#servername)         | 儲存的伺服器名稱`CreatorMap`。

## <a name="inheritance-hierarchy"></a>繼承階層

`CreatorMap`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL::Details

## <a name="activationid"></a>Creatormap:: Activationid

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>參數

*clsid*<br/>
介面識別碼。

*getRuntimeName*<br/>
擷取函式的 Windows 執行階段物件的名稱。

### <a name="remarks"></a>備註

表示透過傳統的 COM 類別識別碼或 Windows 執行階段名稱識別的物件識別碼。

## <a name="factorycache"></a>Creatormap:: Factorycache

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>備註

儲存的處理站快取指標`CreatorMap`。

## <a name="factorycreator"></a>Creatormap:: Factorycreator

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>參數

*currentflags*<br/>
其中一個[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

*entry*<br/>
CreatorMap。

*iidClassFactory*<br/>
Class factory 介面識別碼。

*處理站*<br/>
作業完成時，class factory 的位址。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

建立指定 CreatorMap factory。

## <a name="servername"></a>Creatormap:: Servername

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>備註

儲存 CreatorMap 的伺服器名稱。
