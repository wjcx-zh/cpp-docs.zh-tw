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
ms.openlocfilehash: e716d4952bdb9634cc0d195285d3a65c5c06b0a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336810"
---
# <a name="out_of_memory-class"></a>out_of_memory 類別

當方法因缺少系統或設備記憶體而失敗時引發的異常。

## <a name="syntax"></a>語法

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[out_of_memory建構函數](#ctor)|將 `out_of_memory` 類別的新執行個體初始化。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>需求

**標題:** amprt.h

**命名空間：** 並行

## <a name="out_of_memory"></a><a name="ctor"></a>out_of_memory

初始化類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
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

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)
