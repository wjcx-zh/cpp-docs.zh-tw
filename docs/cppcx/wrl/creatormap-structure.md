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
ms.openlocfilehash: 1527f81694d1d809d585f3f6504c0e6433a2c26b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372606"
---
# <a name="creatormap-structure"></a>CreatorMap 結構

支援 Windows 運行時 C++範本庫基礎結構,並且不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>備註

包含有關如何初始化、註冊和取消註冊物件的資訊。

`CreatorMap`包含下列資訊：

- 如何初始化、註冊和取消註冊物件。

- 如何根據經典 COM 或 Windows 運行時工廠比較啟動數據。

- 有關介面的工廠緩存和伺服器名稱的資訊。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

名稱                                          | 描述
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[建立者對應::啟用 Id](#activationid)     | 表示由經典 COM 類 ID 或 Windows 執行時名稱識別的物件 ID。
[建立者對應:工廠快取](#factorycache)     | 儲存到工廠快取的指標`CreatorMap`。
[創作者地圖::工廠創造者](#factorycreator) | 為指定的`CreatorMap`創建工廠。
[建立者對應:伺服器名稱](#servername)         | 存儲的`CreatorMap`伺服器名稱。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CreatorMap`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間:** 微軟::WRL::D

## <a name="creatormapactivationid"></a><a name="activationid"></a>建立者對應::啟用 Id

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>參數

*Clsid*<br/>
介面識別碼。

*取得 Runtime 名稱*<br/>
檢索物件的 Windows 運行時名稱的函數。

### <a name="remarks"></a>備註

表示由經典 COM 類 ID 或 Windows 執行時名稱識別的物件 ID。

## <a name="creatormapfactorycache"></a><a name="factorycache"></a>建立者對應:工廠快取

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>備註

儲存到工廠快取的指標`CreatorMap`。

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a>創作者地圖::工廠創造者

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>參數

*電流標誌*<br/>
[運行時類類型](runtimeclasstype-enumeration.md)枚舉器之一。

*進入*<br/>
建立者地圖。

*iidClass 工廠*<br/>
類工廠的介面 ID。

*工廠*<br/>
操作完成後,類工廠的位址。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

為指定的建立者映射創建工廠。

## <a name="creatormapservername"></a><a name="servername"></a>建立者對應:伺服器名稱

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>備註

儲存建立者映射的伺服器名稱。
