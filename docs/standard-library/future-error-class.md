---
title: future_error 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::future_error
dev_langs:
- C++
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e5d5c24a658f53dbef4075d68f5aead5454356b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845007"
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
