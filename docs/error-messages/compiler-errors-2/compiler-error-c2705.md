---
title: 編譯器錯誤 C2705
description: 描述 Microsoft C/c + + 編譯器錯誤 C2705。
ms.date: 08/25/2020
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 40d0f70ee379f5d1347b7443817713a53e097f89
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898745"
---
# <a name="compiler-error-c2705"></a>編譯器錯誤 C2705

> '*label*'：不合法的跳入「例外狀況處理常式區塊」範圍

## <a name="remarks"></a>備註

執行會跳到 **`try`** / **`catch`** 、 **`__try`** / **`__except`** 或 **`__try`** / **`__finally`** 區塊內的標籤。 編譯器不允許這種行為。 如需詳細資訊，請參閱 [例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C2705：

```cpp
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```
