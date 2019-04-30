---
title: 編譯器警告 (層級 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 988c1fcbe0826582dceaa527811c688711fd8906
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391838"
---
# <a name="compiler-warning-level-1-c4160"></a>編譯器警告 (層級 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>pragma (pop，...): 未發現之前推入的識別項 '*識別碼*'

## <a name="remarks"></a>備註

原始程式碼中的 pragma 陳述式嘗試快顯尚未推入的識別項。 若要避免這個警告，請確定已正確推入所快顯的識別項。

## <a name="example"></a>範例

下列範例會產生 C4160，並示範如何修正此問題：

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```