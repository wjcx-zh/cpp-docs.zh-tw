---
title: 編譯器警告 C4368 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4368
dev_langs:
- C++
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52026f08a56faa1372b73b94fe91c96682510038
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073209"
---
# <a name="compiler-warning-c4368"></a>編譯器警告 C4368

無法為受管理的 'type' 的成員定義 'member': 不支援混合的類型

無法嵌入原生資料成員設定為 CLR 型別。

不過您可以宣告原生類型的指標，並控制指標在 Managed 類別建構函式和解構函式與完成項中的存留期。 如需詳細資訊，請參閱[解構函式和完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

為錯誤，永遠會發出這個警告。 使用[警告](../../preprocessor/warning.md)pragma 來停用 C4368。

## <a name="example"></a>範例

下列範例會產生 C4368。

```
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```