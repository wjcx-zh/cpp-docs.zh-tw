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
ms.openlocfilehash: 749ef965520732c37457613f44e0a23e213023db
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700969"
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

*程式碼*<br/>
[in]描述發生的錯誤列舉的資料值。

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