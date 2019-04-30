---
title: '#錯誤指示詞 (C /C++)'
ms.date: 11/04/2016
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: dc229a8eae6938cba32787ecbec6a5aa6a17ab47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383981"
---
# <a name="error-directive-cc"></a>#error 指示詞 (C/C++)
**#Error**指示詞會在編譯時期發出使用者指定的錯誤訊息，並終止編譯。

## <a name="syntax"></a>語法

```
#errortoken-string
```

## <a name="remarks"></a>備註

這個指示詞會發出錯誤訊息會包含*語彙基元字串*參數。 *語彙基元字串*參數不是受巨集展開。 這個指示詞在前置處理期間最有用，可通知開發人員程式不一致或條件約束違規。 下列範例會示範前置處理期間的錯誤處理：

```
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)