---
title: 連結器工具錯誤 LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 69af2bd2c22fdb1188cf0b7119791e451e80f966
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686492"
---
# <a name="linker-tools-error-lnk1312"></a>連結器工具錯誤 LNK1312

檔案無效或損毀：無法匯入元件

建立元件時，會將以 **/clr** 編譯的模組或元件以外的檔案傳遞至 **/ASSEMBLYMODULE** 連結器選項。  如果您將物件檔案傳遞至 **/ASSEMBLYMODULE**，只要將物件直接傳遞至連結器，而不是 **/ASSEMBLYMODULE**。

## <a name="examples"></a>範例

下列範例會建立 .obj 檔。

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

下列範例會產生 LNK1312。

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
