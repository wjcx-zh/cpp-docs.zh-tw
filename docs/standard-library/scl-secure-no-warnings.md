---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5dec19d4c7d6f1def451f7f11588f303961cc5c0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

C + + 標準程式庫中呼叫任何可能不安全的方法會導致[編譯器警告 （層級 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要停用此警告，請在程式碼中定義 **_SCL_SECURE_NO_WARNINGS** 巨集：

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

如果您使用先行編譯標頭，此指示詞先行編譯標頭檔中之前，先讓您包含任何 C 執行階段程式庫或標準程式庫標頭。 如果您將其置於個別來源程式碼檔案加入先行編譯標頭檔之前，編譯器會忽略它。

## <a name="remarks"></a>備註

停用警告 C4996 的其他方式包括：

- 使用 [/D (前置處理器定義)](../build/reference/d-preprocessor-definitions.md) 編譯器選項：

   > cl /D_SCL_SECURE_NO_WARNINGS [其他編譯器選項] myfile.cpp

- 使用 [/w](../build/reference/compiler-option-warning-level.md) 編譯器選項：

   > cl /wd4996 [其他編譯器選項] myfile.cpp

- 使用 [#pragma warning](../preprocessor/warning.md) 指示詞：

   ```cpp
   #pragma warning(disable:4996)
   ```

此外，您可以使用 **/w\<l>\<n>** 編譯器選項，手動變更 C4996 警告的層級。 例如，若要將 C4996 警告設為層級 4：

> cl /w44996 [其他編譯器選項] myfile.cpp

如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>另請參閱

[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
