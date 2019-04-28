---
title: 編譯器錯誤 C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 33860273db07894a9a4d15ba6d578598a18819ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208053"
---
# <a name="compiler-error-c3836"></a>編譯器錯誤 C3836

靜態建構函式不可以有成員初始設定式清單

受管理的類別不能有靜態建構函式，也有成員初始設定清單。 靜態類別建構函式會呼叫 common language runtime 不要類別初始化，初始化靜態資料成員。

## <a name="example"></a>範例

下列範例會產生 C3836:

```
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
