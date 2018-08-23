---
title: 'Safeintexception:: Safeintexception |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c5fd1e2194ece9435b219a410c8ad49eb95137a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598554"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException

會建立**SafeIntException**物件。

## <a name="syntax"></a>語法

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>參數

[in]*程式碼*  
描述發生的錯誤列舉的資料值。

## <a name="remarks"></a>備註

可能值*程式碼*Safeint.h 檔案中所定義。 為了方便起見，可能的值也會列出以下。

- `SafeIntNoError`

- `SafeIntArithmeticOverflow`

- `SafeIntDivideByZero`

## <a name="requirements"></a>需求

**標頭：** safeint.h

**命名空間：** msl:: utilities

## <a name="see-also"></a>另請參閱

[SafeInt 程式庫](../windows/safeint-library.md)  
[SafeIntException 類別](../windows/safeintexception-class.md)  
[SafeInt 類別](../windows/safeint-class.md)