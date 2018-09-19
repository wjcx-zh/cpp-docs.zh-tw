---
title: __based 文法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e9074de25d8cb914432123478f5f338ff4ba1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103760"
---
# <a name="based-grammar"></a>__based 文法

## <a name="microsoft-specific"></a>Microsoft 特定的

基底位址在您需要精確控制配置物件的區段時很實用 (靜態和動態架構資料)。

基底定址在 32 位元和 64 位元編譯中可接受 「 型的指標 」 的唯一形式所定義的類型包含 32 位元或 64 位元的基底的 32 位元或 64 位元的移動，或根據**void**。

## <a name="grammar"></a>文法

*根據範圍修飾詞*: **__based (***基底運算式***)** 

*基底運算式*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*以變數*:*識別碼*

*架構抽象宣告子*:*抽象宣告子*

*基底型別*:*型別名稱*

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[Based 指標](../cpp/based-pointers-cpp.md)