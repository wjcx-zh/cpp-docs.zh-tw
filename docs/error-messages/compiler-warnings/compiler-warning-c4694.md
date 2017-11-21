---
title: "編譯器警告 C4694 |Microsoft 文件"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: article
f1_keywords: C4694
dev_langs: C++
helpviewer_keywords: C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1af20859e394fe62403358107b74f9d1df5facb1
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-c4694"></a>編譯器警告 C4694

> '*類別*': 密封抽象類別不能有基底類別'*base_class*'

抽象和密封類別無法從參考類型繼承，密封和抽象類別無法實作基底類別函式，也不允許自己用作為基底類別。

如需詳細資訊，請參閱[抽象](../../windows/abstract-cpp-component-extensions.md)，[密封](../../windows/sealed-cpp-component-extensions.md)，和[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。

## <a name="example"></a>範例

下列範例會產生 C4694。

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```