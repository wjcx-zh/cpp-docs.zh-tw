---
title: 編譯器錯誤 C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: cf682bf14246754cca74a43dffc39761ff6125c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395322"
---
# <a name="compiler-error-c2978"></a>編譯器錯誤 C2978

語法錯誤: 必須是 'keyword1' 或 'keyword２'，但找到的是類型 'keyword3'; 泛型中不支援非類型參數

泛型類別宣告不正確。 請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C2978。

```
// C2978.cpp
// compile with: /clr /c
generic <ref class T>   // C2978
// try the following line instead
// generic <typename T>   // OK
ref class Utils {
   static void sort(T elems, size_t size);
};

generic <int>
// try the following line instead
// generic <class T>
ref class Utils2 {
   static void sort(T elems, size_t size);
};
```