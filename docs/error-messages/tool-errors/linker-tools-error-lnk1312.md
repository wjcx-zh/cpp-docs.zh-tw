---
title: 連結器工具錯誤 LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: e462d24f2eb54718ba73617146aab96bb14a66df
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990914"
---
# <a name="linker-tools-error-lnk1312"></a>連結器工具錯誤 LNK1312

檔案無效或損毀：無法匯入元件

建立元件時，會將使用 **/clr**編譯之模組或元件以外的檔案傳遞給 **/ASSEMBLYMODULE**連結器選項。  如果您將物件檔傳遞至 **/ASSEMBLYMODULE**，只要直接將物件傳遞給連結器，而不是 **/ASSEMBLYMODULE**。

## <a name="example"></a>範例

下列範例會建立 .obj 檔案。

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>範例

下列範例會產生 LNK1312。

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
