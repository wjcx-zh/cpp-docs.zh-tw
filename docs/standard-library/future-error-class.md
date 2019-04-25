---
title: future_error 類別
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: 2b3f754c0ceb7384d99c6a657de214d30aca24b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159752"
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

**標頭：** \<未來 >

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[logic_error 類別](../standard-library/logic-error-class.md)<br/>
[error_code 類別](../standard-library/error-code-class.md)<br/>
