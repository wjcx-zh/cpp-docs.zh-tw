---
title: static 儲存類別規範
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: e84e2745c6077f038f47295119936a1ad6431bdd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229489"
---
# <a name="static-storage-class-specifier"></a>static 儲存類別規範

在內部層級使用儲存類別指定名稱宣告的變數 **`static`** 具有全域存留期，但是只有在宣告它的區塊內才可見。 對於常數位符串，使用 **`static`** 很有用，因為它可減輕經常呼叫的函式中經常初始化的額外負荷。

## <a name="remarks"></a>備註

如果您未明確初始化 **`static`** 變數，則預設會將其初始化為0。 在函式內， **`static`** 會配置儲存體並作為定義。 內部靜態變數會提供只有單一函式可見的私用永久儲存區。

## <a name="see-also"></a>另請參閱

[C 儲存類別](c-storage-classes.md)<br/>
[儲存類別 (C++)](../cpp/storage-classes-cpp.md)
