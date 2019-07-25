---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: d19d47fe7120301740e1431765fc6edbeaa48c60
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448198"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

呼叫C++標準程式庫中任何可能不安全的方法, 會產生[編譯器警告 (層級 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要停用這個警告, 請在您的程式碼中定義宏 _SCL_SECURE_NO_WARNINGS:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

如果您使用先行編譯的標頭, 請將此指示詞放在先行編譯標頭檔中, 再包含任何 C 執行時間程式庫或標準程式庫標頭。 如果您在包含先行編譯標頭檔之前, 將它放在個別的原始程式碼檔案中, 編譯器會忽略它。

## <a name="remarks"></a>備註

停用警告 C4996 的其他方式包括：

- 使用 [/D (前置處理器定義)](../build/reference/d-preprocessor-definitions.md) 編譯器選項：

   > cl/D_SCL_SECURE_NO_WARNINGS [其他編譯器選項] myfile.txt .cpp

- 使用 [/w](../build/reference/compiler-option-warning-level.md) 編譯器選項：

   > cl/wd4996 [其他編譯器選項] myfile.txt .cpp

- 使用 [#pragma warning](../preprocessor/warning.md) 指示詞：

   ```cpp
   #pragma warning(disable:4996)
   ```

此外，您可以使用 **/w\<l>\<n>** 編譯器選項，手動變更 C4996 警告的層級。 例如，若要將 C4996 警告設為層級 4：

> cl/w44996 [其他編譯器選項] myfile.txt .cpp

如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>另請參閱

[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)
