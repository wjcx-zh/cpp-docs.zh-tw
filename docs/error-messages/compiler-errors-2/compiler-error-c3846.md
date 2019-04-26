---
title: 編譯器錯誤 C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 788f03e4364404ad5c30b7edcba8b743c7f201ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152419"
---
# <a name="compiler-error-c3846"></a>編譯器錯誤 C3846

'symbol': 無法匯入從 'assembly2' 的符號: 'symbol' 已從另一個組件 'assembly1' 匯入

不能從參考的組件匯符號，因為它先前已從參考的組件匯入。

## <a name="example"></a>範例

下列範例會產生 C3846:

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

然後再編譯這個：

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
