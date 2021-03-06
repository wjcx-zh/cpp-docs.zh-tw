---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 0ea02806cae3295af0846baa6c4e9049d54c271b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75315169"
---
# <a name="comm"></a>COMM

使用*定義*中指定的屬性建立微乎其微變數。

## <a name="syntax"></a>語法

> **通訊***定義*⟦ __，__ *定義*.。。⟧

## <a name="remarks"></a>備註

微乎其微變數是由連結器所配置，而且無法初始化。 這表示您不能依賴這類變數的位置或順序。

每個*定義*的格式如下：

⟦*語言類型*⟧⟦**近** | **遠**⟧_標籤_ **：** _輸入_⟦ **：** _count_⟧

*語言類型*、 **NEAR**和**FAR**引數只在32位 MASM 中有效。

選擇性的*語言類型*會為後面的名稱設定命名慣例。 它會覆寫所指定的任何語言 **。MODEL**指示詞。 選擇性的**接近**或**遠**會覆寫目前的記憶體模型。 *標籤*是變數的名稱。 *類型*可以是任何類型規範（[BYTE](byte-masm.md)、 [WORD](word.md)等等）或指定位元組數目的整數。 選擇性*計數*會指定宣告之資料物件中的元素數目。 預設*計數*為一。

## <a name="example"></a>範例

這個範例會建立512位元組元素的陣列：

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
