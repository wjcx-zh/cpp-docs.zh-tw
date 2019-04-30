---
title: 編譯器錯誤 C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: fb4a0e6f3f6ec227b978ae0b7d3864b2134de986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406817"
---
# <a name="compiler-error-c2834"></a>編譯器錯誤 C2834

'operator operator' 必須全域限定

`new`和`delete`運算子會繫結至類別所在的位置。 範圍解析不能選取的版本`new`或`delete`自其他類別。 若要實作的多種形式`new`或`delete`運算子，使用額外的型式參數建立運算子版本。