---
title: 編譯器錯誤 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 00952e55f1b732bd9af3733f5c0ec575a39116fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202102"
---
# <a name="compiler-error-c2818"></a>編譯器錯誤 C2818

多載 ' operator-> ' 的應用程式是遞迴到類型 ' type '

類別成員存取運算子的重新定義包含遞迴 `return` 語句。 若要使用遞迴來重新定義 `->` 運算子，您必須將遞迴常式移至運算子 override 函式所呼叫的另一個函數。
