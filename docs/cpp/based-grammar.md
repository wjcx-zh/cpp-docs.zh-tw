---
title: __based 文法
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 8dec9b0bcc7db25e2ec4c39b9d907922691bfc05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393944"
---
# <a name="based-grammar"></a>__based 文法

## <a name="microsoft-specific"></a>Microsoft 特定的

基底位址在您需要精確控制配置物件的區段時很實用 (靜態和動態架構資料)。

基底定址在 32 位元和 64 位元編譯中可接受 「 型的指標 」 的唯一形式所定義的類型包含 32 位元或 64 位元的基底的 32 位元或 64 位元的移動，或根據**void**。

## <a name="grammar"></a>文法

*based-range-modifier*: **__based(**  *base-expression*  **)**

*base-expression*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*以變數*:*識別碼*

*based-abstract-declarator*: *abstract-declarator*

*基底型別*:*型別名稱*

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[Based 指標](../cpp/based-pointers-cpp.md)