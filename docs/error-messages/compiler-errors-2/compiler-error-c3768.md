---
title: 編譯器錯誤 C3768 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3768
dev_langs:
- C++
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6b7a2d1617591609f75b2b07f1a94983ee22f4
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704954"
---
# <a name="compiler-error-c3768"></a>編譯器錯誤 C3768

> 無法取得純 managed 程式碼中的虛擬 vararg 函式的位址

## <a name="remarks"></a>備註

**/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

編譯時 **/clr: pure**，您無法取得虛擬機器的位址`vararg`函式。

## <a name="example"></a>範例

下列範例會產生 C3768:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```