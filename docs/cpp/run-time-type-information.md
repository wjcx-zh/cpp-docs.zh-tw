---
title: 執行階段類型資訊 |Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f9ce0094bce1f8e7590cef0cbe3bfe85f35158d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056057"
---
# <a name="run-time-type-information"></a>執行階段類型資訊

執行階段類型資訊 (RTTI) 是一項機制，可在程式執行期間判斷物件的類型。 C++ 語言中加入 RTTI 的原因在於，有許多類別庫的廠商本身實作這項功能。 這樣會導致程式庫之間不相容。 因此，在語言層級支援執行階段類型資訊的需求變得很明確。

為避免混淆，這裡討論的 RTTI 幾乎完全限於指標。 不過，所討論的概念也適用於參考。

執行階段類型資訊有三個主要的 C++ 語言項目：

- [Dynamic_cast](../cpp/dynamic-cast-operator.md)運算子。

   用於多型類型的轉換。

- [Typeid](../cpp/typeid-operator.md)運算子。

   用於識別物件的實際類型。

- [Type_info](../cpp/type-info-class.md)類別。

   用來保存所傳回的型別資訊**typeid**運算子。

## <a name="see-also"></a>另請參閱

[轉型](../cpp/casting.md)