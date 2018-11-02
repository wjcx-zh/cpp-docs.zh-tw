---
title: virtual (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: f68bd2e500ebe16c43ef6c3d7a5aede26421b27d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605058"
---
# <a name="virtual-c"></a>virtual (C++)

**虛擬**關鍵字會宣告虛擬函式或虛擬基底類別。

## <a name="syntax"></a>語法

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>參數

*類型規範*<br/>
指定虛擬成員函式的傳回型別。

*成員函式宣告子*<br/>
宣告成員函式。

*存取規範*<br/>
基底類別，定義存取層級**公用**，**保護**或是**私人**。 可以出現在前後**虛擬**關鍵字。

*基底類別名稱*<br/>
識別先前宣告的類別類型。

## <a name="remarks"></a>備註

請參閱[虛擬函式](../cpp/virtual-functions.md)如需詳細資訊。

另請參閱下列關鍵字：[類別](../cpp/class-cpp.md)，[私人](../cpp/private-cpp.md)，[公用](../cpp/public-cpp.md)，以及[保護](../cpp/protected-cpp.md)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)