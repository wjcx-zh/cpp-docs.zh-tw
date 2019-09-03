---
title: '#error 指示詞 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: bfb5c18f20319e6e6d345f28d3e1850714334b71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216117"
---
# <a name="error-directive-cc"></a>#error 指示詞 (CC++/)

**#Error**指示詞會在編譯時期發出使用者指定的錯誤訊息, 然後終止編譯。

## <a name="syntax"></a>語法

> **#error***token-字串*

## <a name="remarks"></a>備註

這個指示詞發出的錯誤訊息包含*token 字串*參數。 *Token 字串*參數不受宏擴充的制約。 這個指示詞在前置處理期間最為有用, 可通知開發人員程式不一致, 或違反條件約束。 下列範例會示範前置處理期間的錯誤處理：

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)
