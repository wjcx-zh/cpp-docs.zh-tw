---
title: 編譯器錯誤 C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 828e5bbca0b796864ec8b364ee69c18a3b5eea00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206944"
---
# <a name="compiler-error-c2170"></a>編譯器錯誤 C2170

' identifier '：未宣告為函式，不可為內建函式

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Pragma `intrinsic` 用於函式以外的專案。

1. Pragma `intrinsic` 用於沒有內建表單的函式。
