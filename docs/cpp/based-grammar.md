---
title: __based 文法
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: a8c923b5a111144c539b5bea1b2f47eb58dd1fbd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857641"
---
# <a name="__based-grammar"></a>__based 文法

**Microsoft 專屬**

基底位址在您需要精確控制配置物件的區段時很實用 (靜態和動態架構資料)。

32位和64位編譯中可接受的唯一定址形式是「以指標為基礎」，其定義一個類型，其中包含對32位或64位基底或以**void**為基礎的32位或64位置換。

## <a name="grammar"></a>文法

以*範圍為基礎的修飾*詞： **__based （** *基底運算式* **）**

以*運算式為基礎*的*variablebased-abstract-declaratorsegment-namesegment-cast*

以*變數為基礎*：*識別碼*

*型-抽象*-宣告子：*抽象-* 宣告子

*基底類型*：*類型-名稱*

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[Based 指標](../cpp/based-pointers-cpp.md)