---
title: 編譯器錯誤 C3227 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3227
dev_langs:
- C++
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddf2ec945a8bdbe103631d8346641e1370eda216
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096622"
---
# <a name="compiler-error-c3227"></a>編譯器錯誤 C3227

'parameter': 無法使用 'keyword' 配置的泛型型別

若要具現化型別，適當的建構函式是必要的。 不過，編譯器就無法確保適當的建構函式可使用。

您可以使用範本而不是泛型來解決這個錯誤，或您可以使用數種方法之一來建立型別的執行個體。

## <a name="example"></a>範例

下列範例會產生 C3227。

```
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```