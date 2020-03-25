---
title: 編譯器錯誤 C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 99f3644869f6c5395684643f0e7802f3a01baa62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205357"
---
# <a name="compiler-error-c2439"></a>編譯器錯誤 C2439

' identifier '：無法初始化成員

無法初始化類別、結構或等位成員。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 嘗試初始化間接基類或結構。

1. 嘗試初始化類別或結構的繼承成員。 繼承的成員必須由類別或結構的「函式」初始化。
