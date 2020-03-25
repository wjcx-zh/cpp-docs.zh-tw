---
title: 編譯器警告 (層級 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 7de4cdf0eacb1b9848a4350f1d223da1fd47d1fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198298"
---
# <a name="compiler-warning-level-4-c4611"></a>編譯器警告 (層級 4) C4611

' function ' 和C++ object 析構之間的互動是不可移植的

在某些平臺上，包含**catch**的函式在C++超出範圍時，可能不支援析構的物件語義。

為避免非預期的行為，請避免在具有函式和析構函數的函式中使用**catch** 。

這個警告只會發出一次;請參閱[pragma warning](../../preprocessor/warning.md)。
