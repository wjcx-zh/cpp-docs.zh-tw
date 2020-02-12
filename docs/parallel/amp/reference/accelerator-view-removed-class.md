---
title: accelerator_view_removed 類別
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 9a3f6f349fc3103893639fe209dcf23a07ffec56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127120"
---
# <a name="accelerator_view_removed-class"></a>accelerator_view_removed 類別

當基礎 DirectX 呼叫因 Windows 超時偵測和復原機制而失敗時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[accelerator_view_removed 的構造函式](#ctor)|初始化 `accelerator_view_removed` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|傳回 HRESULT 錯誤碼，指出 `accelerator_view` 物件移除的原因。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** 並行

## <a name="ctor"></a>accelerator_view_removed

初始化[accelerator_view_removed](accelerator-view-removed-class.md)類別的新實例。

### <a name="syntax"></a>語法

```cpp
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>參數

*message*<br/>
錯誤的描述。

*view_removed_reason*<br/>
HRESULT 錯誤碼，表示移除 `accelerator_view` 物件的原因。

### <a name="return-value"></a>傳回值

`accelerator_view_removed` 類別的新執行個體。

## <a name="get_view_removed_reason"></a>get_view_removed_reason

傳回 HRESULT 錯誤碼，指出 `accelerator_view` 物件移除的原因。

### <a name="syntax"></a>語法

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
