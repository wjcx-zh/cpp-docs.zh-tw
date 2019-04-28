---
title: out_of_memory 類別
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: ab498935039fad584220a84c388e337ee090c57d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351179"
---
# <a name="outofmemory-class"></a>out_of_memory 類別

方法失敗，因為系統或裝置的記憶體不足時，會擲回例外狀況。

## <a name="syntax"></a>語法

```
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[out_of_memory 建構函式](#ctor)|初始化 `out_of_memory` 類別的新執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** 並行
## <a name="ctor"></a> out_of_memory

初始化類別的新執行個體。

### <a name="syntax"></a>語法

```
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述。

### <a name="return-value"></a>傳回值

`out_of_memory` 類別的新執行個體。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
