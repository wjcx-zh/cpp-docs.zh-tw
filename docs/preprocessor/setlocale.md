---
title: setlocale |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs:
- C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa68389b804452e2a17b9880978cd56d291cefb6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079411"
---
# <a name="setlocale"></a>setlocale

定義轉譯寬字元常數和字串常值時使用的地區設定 (國家/地區和語言)。

## <a name="syntax"></a>語法

```
#pragma setlocale( "[locale-string]" )
```

## <a name="remarks"></a>備註

由於將多位元組字元轉換為寬字元的演算法因地區設定而異，或者編譯和可執行檔將執行的位置可能使用不同的地區設定，因此這個 pragma 提供在編譯時期指定目標地區設定的方法。 這樣可以確保能夠以正確的格式儲存寬字元字串。

預設值*地區設定字串*是""。

"C"地區設定對應至為其值的字串中的每個字元**wchar_t** （不帶正負號短）。 其他值的有效值`setlocale`中找到這些項目[語言字串](../c-runtime-library/language-strings.md)清單。 例如，您可以發出：

```cpp
#pragma setlocale("dutch")
```

能否發出語言字串取決於電腦的字碼頁和語言 ID 支援。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)