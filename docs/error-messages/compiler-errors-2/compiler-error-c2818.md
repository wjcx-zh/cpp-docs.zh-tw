---
title: 編譯器錯誤 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 786a38aca2c3b9674969018d9e5766eed29c358c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212666"
---
# <a name="compiler-error-c2818"></a>編譯器錯誤 C2818

多載 ' operator-> ' 的應用程式是遞迴到類型 ' type '

類別成員存取運算子的重新定義包含遞迴 **`return`** 語句。 若要使用遞迴來重新定義 `->` 運算子，您必須將遞迴常式移至運算子 override 函式所呼叫的另一個函數。
