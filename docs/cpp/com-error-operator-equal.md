---
title: _com_error::operator = |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= _com_error objects
- = operator [C++], with specific Visual C++ objects
- operator = _com_error objects
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2fe53c7040bc248d63bd3d14f90f915bdcd689a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061028"
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

*,*<br/>
`_com_error` 物件。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)