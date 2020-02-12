---
title: invalid_operation 類別
ms.date: 11/04/2016
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
ms.openlocfilehash: e17d530569d16ba0084a58bf0be00d4a8423b7f6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140874"
---
# <a name="invalid_operation-class"></a>invalid_operation 類別

這個類別描述執行無效的作業，且並行執行階段擲回的另一個例外狀況類型未正確描述該作業時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class invalid_operation : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_operation](#ctor)|已多載。 建構 `invalid_operation` 物件。|

## <a name="remarks"></a>備註

擲回這個例外狀況的各種方法，通常會記錄它們擲回此例外狀況的情形。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`invalid_operation`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>invalid_operation

建構 `invalid_operation` 物件。

```cpp
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
