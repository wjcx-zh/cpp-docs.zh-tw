---
title: "編譯器警告 C4693 |Microsoft 文件"
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4693
dev_langs: C++
helpviewer_keywords: C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e5d7b93295505d989e651500dda0664c1a13a36
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-c4693"></a>編譯器警告 C4693

> 'class': 密封的抽象類別不能有任何執行個體成員 'Test'

如果類型標記[密封](../../windows/sealed-cpp-component-extensions.md)和[抽象](../../windows/abstract-cpp-component-extensions.md)，它只能有靜態成員。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。

## <a name="example"></a>範例

下例會產生 C4693。

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```