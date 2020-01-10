---
title: 編譯器錯誤 C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 4da6616c59ea4b8a720c8e2dc9742e37a9939171
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738761"
---
# <a name="compiler-error-c3201"></a>編譯器錯誤 C3201

類別範本 'template' 的樣板參數清單不符合範本參數 'template' 的範本參數清單

您將引數中的類別範本傳遞至不接受範本參數的類別範本，或是為預設範本引數傳遞了數目不符的範本引數。

```cpp
// C3201.cpp
template<typename T1, typename T2>
class X1
{
};

template<template<typename T> class U = X1>   // C3201
class X2
{
};

template<template<typename T, typename V> class U = X1>   // OK
class X3
{
};
```
