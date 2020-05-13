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
ms.openlocfilehash: e118d7e3cce47ebb93cef16319a8fc45aab1118b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349943"
---
# <a name="safeintexception-class"></a>SafeIntException 類別

`SafeInt` 類別使用 `SafeIntException` 來識別數學運算為何無法完成。

> [!NOTE]
> 此函式庫的最新[https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)版本 。

## <a name="syntax"></a>語法

```cpp
class SafeIntException;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                    | 描述
------------------------------------------------------- | ------------------------------------
[安全例外:安全例外](#safeintexception) | 建立 `SafeIntException` 物件。

## <a name="remarks"></a>備註

[SafeInt 類別](../safeint/safeint-class.md)是唯一使用 `SafeIntException` 類別的類別。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SafeIntException`

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** msl:: utilities

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>安全例外:安全例外

建立 `SafeIntException` 物件。

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>參數

*代碼*<br/>
[in] 描述發生之錯誤的列舉資料值。

### <a name="remarks"></a>備註

*code* 的可能值定義在 Safeint.h 檔案中。 為了方便起見，這裡也列出可能的值。

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
