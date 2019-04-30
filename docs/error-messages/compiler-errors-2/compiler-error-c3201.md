---
title: 編譯器錯誤 C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 92e068103563f7427de7b394536e72b06fab3374
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402758"
---
# <a name="compiler-error-c3201"></a>編譯器錯誤 C3201

類別範本 'template' 的樣板參數清單不符合範本參數 'template' 的範本參數清單

您將引數中的類別範本傳遞至不接受範本參數的類別範本，或是為預設範本引數傳遞了數目不符的範本引數。

```
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