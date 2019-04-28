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
ms.openlocfilehash: 77c60aed511fc3dbbea2d74e83e36dae735dcb0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348304"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

呼叫任何可能不安全的方法，在C++標準程式庫會導致[編譯器警告 （層級 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要停用這個警告，請定義巨集 _SCL_SECURE_NO_WARNINGS 程式碼中：

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

如果您使用先行編譯標頭，將此指示詞放先行編譯標頭檔中加入任何 C 執行階段程式庫或標準程式庫標頭之前。 如果您將它放入個別來源程式碼檔案加入先行編譯標頭檔之前，編譯器會忽略它。

## <a name="remarks"></a>備註

停用警告 C4996 的其他方式包括：

- 使用 [/D (前置處理器定義)](../build/reference/d-preprocessor-definitions.md) 編譯器選項：

   > cl /D_SCL_SECURE_NO_WARNINGS [其他編譯器選項] myfile.cpp

- 使用 [/w](../build/reference/compiler-option-warning-level.md) 編譯器選項：

   > cl /wd4996 [other compiler options] myfile.cpp

- 使用 [#pragma warning](../preprocessor/warning.md) 指示詞：

   ```cpp
   #pragma warning(disable:4996)
   ```

此外，您可以使用 **/w\<l>\<n>** 編譯器選項，手動變更 C4996 警告的層級。 例如，若要將 C4996 警告設為層級 4：

> cl /w44996 [other compiler options] myfile.cpp

如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>另請參閱

[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
