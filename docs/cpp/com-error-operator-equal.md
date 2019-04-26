---
title: _com_error::operator =
ms.date: 11/04/2016
f1_keywords:
- _com_error::operator=
helpviewer_keywords:
- operator= _com_error objects
- = operator [C++], with specific Visual C++ objects
- operator = _com_error objects
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
ms.openlocfilehash: 68eb486ec109d98890ebf3adc0c086368380142b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154990"
---
# <a name="comerroroperator-"></a>_com_error::operator =

**Microsoft 專屬**

將現有的 `_com_error` 物件指派給另一個物件。

## <a name="syntax"></a>語法

```
_com_error& operator = (
   const _com_error& that
) throw ( );
```

#### <a name="parameters"></a>參數

*that*<br/>
`_com_error` 物件。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)