---
title: 編譯器錯誤 C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 5173b1c0df7de6a4e8d9993e680b961a82bb10a7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738462"
---
# <a name="compiler-error-c3366"></a>編譯器錯誤 C3366

' variable '： managed 或 WinRTtypes 的靜態資料成員必須在類別定義內定義

您嘗試參考的 WinRT 或 .NET 類別或介面的靜態成員不在該類別或介面的定義範圍內。

編譯器必須知道類別的完整定義 (以在一個階段後發出中繼資料) ，且需要靜態資料成員在該類別內初始化。

例如，下列範例會產生 C3366，並說明如何加以修正：

```cpp
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
