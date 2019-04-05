---
title: 編譯器錯誤 C3831
ms.date: 11/04/2016
f1_keywords:
- C3831
helpviewer_keywords:
- C3831
ms.assetid: a125d8dc-b75a-4ea0-b6c7-fe7b119dba25
ms.openlocfilehash: d9aa703f12fd175d9f7fc00eb76e76097a32e860
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781662"
---
# <a name="compiler-error-c3831"></a>編譯器錯誤 C3831

'member': 'class' 不能有固定的資料成員或成員函式會傳回 pin 指標

[pin_ptr (C + + /cli CLI)](../../extensions/pin-ptr-cpp-cli.md)的使用方式錯誤。

## <a name="example"></a>範例

下列範例會產生 C3831:

```
// C3831a.cpp
// compile with: /clr
ref class Y
{
public:
   int i;
};

ref class X
{
   pin_ptr<int> mbr_Y;   // C3831
   int^ mbr_Y2;   // OK
};

int main() {
   Y y;
   pin_ptr<int> p = &y.i;
}
```
