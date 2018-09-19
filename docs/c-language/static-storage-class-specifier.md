---
title: static 儲存類別規範 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1a58a8c7ab6eeb7d304d84cef15beb9046184fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079488"
---
# <a name="static-storage-class-specifier"></a>static 儲存類別規範

在內部層級使用 **static** 儲存類別指定名稱宣告的變數具有全域存留期，但是只有在宣告該變數的區塊內才看得見。 若是常數字串，使用 **static** 會很有用，因為它可減輕經常呼叫的函式中經常需要初始化的額外負荷。

## <a name="remarks"></a>備註

如果您未明確初始化 **static** 變數，該變數預設會初始化為 0。 在函式內，**static** 會配置儲存區並且做為定義。 內部靜態變數會提供只有單一函式可見的私用永久儲存區。

## <a name="see-also"></a>請參閱

[C 儲存類別](c-storage-classes.md)<br/>
[儲存類別 (C++)](../cpp/storage-classes-cpp.md)