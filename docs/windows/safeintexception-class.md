---
title: SafeIntException 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ffd82f80b8af0b53ca86ca3daded84580e1e07b
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235733"
---
# <a name="safeintexception-class"></a>SafeIntException 類別

`SafeInt`類別會使用`SafeIntException`來找出原因無法完成數學運算。

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
