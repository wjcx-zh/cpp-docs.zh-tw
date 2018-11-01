---
title: SafeIntException 類別
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: 80a1573c2f43b1f4b31731083974f87ba389fac2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566656"
---
# <a name="safeintexception-class"></a>SafeIntException 類別

`SafeInt`類別會使用`SafeIntException`來找出原因無法完成數學運算。

> [!NOTE]
> 此程式庫的最新版本是位於[ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt)。

## <a name="syntax"></a>語法

```cpp
class SafeIntException;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                    | 描述
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | 建立 `SafeIntException` 物件。

## <a name="remarks"></a>備註

[SafeInt 類別](../windows/safeint-class.md)是唯一的類別，會使用`SafeIntException`類別。

## <a name="inheritance-hierarchy"></a>繼承階層

`SafeIntException`

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** msl:: utilities

## <a name="safeintexception"></a>Safeintexception:: Safeintexception

建立 `SafeIntException` 物件。

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>參數

*程式碼*<br/>
[in]描述發生的錯誤列舉的資料值。

### <a name="remarks"></a>備註

可能值*程式碼*Safeint.h 檔案中所定義。 為了方便起見，可能的值也會列出以下。

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
