---
title: 連結器工具錯誤 LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 49fa7e7963d6bb561e1602b58fe1f26c5f3d54bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160467"
---
# <a name="linker-tools-error-lnk1312"></a>連結器工具錯誤 LNK1312

檔案無效或損毀： 無法匯入組件

建置組件、 模組或編譯的組件以外的檔案時 **/clr**已傳遞給 **/ASSEMBLYMODULE**連結器選項。  如果您傳遞的物件檔 **/ASSEMBLYMODULE**，只是物件直接傳遞給連結器，而不是以 **/ASSEMBLYMODULE**。

## <a name="example"></a>範例

下列範例所建立的.obj 檔案。

```
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>範例

下列範例會產生 LNK1312。

```
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```