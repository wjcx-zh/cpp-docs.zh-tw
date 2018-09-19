---
title: 編譯器錯誤 C2842 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20967ab4cd047f62a5cf692c91fec90148b4f470
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118813"
---
# <a name="compiler-error-c2842"></a>編譯器錯誤 C2842

'class'：Managed 或 WinRT 類型不可以定義其自身的 'operator new' 或 'operator delete'

您也可以定義自己 * * 運算子 new 或**運算子 delete**管理原生堆積上的記憶體配置。 不過，參考類別不能定義這些運算子，因為它們只會配置於 Managed 堆積上。


如需詳細資訊，請參閱 <<c0> [ 使用者定義的運算子 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C2842。

```
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
