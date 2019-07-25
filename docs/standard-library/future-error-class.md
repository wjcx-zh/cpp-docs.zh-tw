---
title: future_error 類別
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: ed3f9d63c45d0e185e3e1476094736d132822173
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447353"
---
# <a name="futureerror-class"></a>future_error 類別

描述可由管理 [future](../standard-library/future-class.md) 物件之類型的方法擲回的例外狀況物件。

## <a name="syntax"></a>語法

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>需求

**標頭:** \<未來 >

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[logic_error 類別](../standard-library/logic-error-class.md)\
[error_code 類別](../standard-library/error-code-class.md)
